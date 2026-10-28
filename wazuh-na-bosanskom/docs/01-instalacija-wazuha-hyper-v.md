# Instalacija Wazuha na Hyper-V — vodič na bosanskom

- **Nivo:** početni
- **Namjena:** edukativni laboratorij (lab)
- **Host:** Windows s Hyper-V ulogom
- **Guest OS:** Ubuntu Server 24.04 LTS, 64-bit
- **Wazuh:** 4.14.x stable grana; provjeri posljednje stabilno izdanje prije izvođenja
- **Zadnja provjera vodiča:** 2026-10-27
- **Status provjere:** početni nacrt — označi kao testirano tek nakon što lično prođeš sve korake

> Ovaj vodič postavlja Wazuh server, indexer i dashboard na jednoj virtualnoj mašini (all-in-one). To je prikladno za učenje i mali lab, ali nije automatski preporuka za produkciju.

## 1. Šta ćemo napraviti?

Wazuh centralna instalacija sadrži tri glavne komponente:

- **Wazuh server / manager** — obrađuje podatke agenata i generiše sigurnosna upozorenja.
- **Wazuh indexer** — indeksira i pohranjuje podatke za pretragu.
- **Wazuh dashboard** — web sučelje za pregled i analizu.

U ovom vodiču instalirat ćemo sve tri komponente na jednoj Ubuntu virtualnoj mašini (VM). Nakon instalacije pristupit ćemo dashboardu preko privatne IP adrese.

## 2. Preduvjeti i resursi

Službeni Wazuh Quickstart za mali broj agenata navodi preporučene resurse od 4 vCPU-a, 8 GiB RAM-a i 50 GB prostora za pohranu za raspon od 1–25 agenata. Stvarna potrošnja zavisi od količine događaja, pravila i perioda zadržavanja podataka.

Za ugodan laboratorijski rad preporuka ovog vodiča je:

| Resurs | Početna postavka |
|---|---|
| Virtualni procesori | 4 vCPU |
| RAM | 8–12 GiB |
| Virtualni disk | 80–100 GB, dinamički ili fiksni prema potrebama |
| Mreža | Privatni ili interni Hyper-V virtualni switch; NAT je opcija ako je potrebno |
| Operativni sistem | Ubuntu Server 24.04 LTS x86_64 |
| Pristup | Konzola Hyper-V i SSH samo iz pouzdane mreže, ako je omogućen |

**Napomena:** dinamički VHDX može rasti do maksimalne veličine, ali fizički prostor na hostu i dalje mora biti dostupan. Nemoj dodijeliti VM-u više RAM-a nego što host može stabilno podnijeti.

Potrebno je:
- Windows host s Hyper-V omogućenim i dovoljno slobodnih resursa.
- ISO datoteka Ubuntu Server 24.04 LTS preuzeta sa zvanične Ubuntu stranice.
- Internet pristup iz VM-a radi preuzimanja paketa.
- Privatna IP adresa ili DHCP rezervacija koju možeš pronaći.
- Administratorski pristup Ubuntu VM-u.

## 3. Napravi virtualni switch u Hyper-V-u

1. Otvori **Hyper-V Manager**.
2. U desnom panelu odaberi **Virtual Switch Manager**.
3. Za jednostavan lab odaberi odgovarajući tip:
   - **External**: VM je povezana s fizičkom mrežom. Koristi samo ako je dozvoljeno i razumiješ mrežne posljedice.
   - **Internal**: komunikacija između hosta i VM-ova; internet nije automatski dostupan.
   - **Private**: komunikacija samo između VM-ova na tom switchu.
4. Dodijeli naziv, npr. `Wazuh-Lab-Switch`, i sačuvaj promjene.

Za početnika je praktičan Internal switch uz kontrolisan NAT ili External switch na pouzdanoj laboratorijskoj mreži. Nemoj izlagati Wazuh dashboard direktno internetu.

## 4. Kreiraj Ubuntu virtualnu mašinu

1. U Hyper-V Manageru izaberi **New → Virtual Machine**.
2. Naziv: `Wazuh-Lab`.
3. Generacija: **Generation 2**.
4. Dodijeli memoriju od 8192 MB ili više. Ako je dostupno, možeš uključiti Dynamic Memory, ali za predvidljiv laboratorijski rad fiksni RAM je jednostavniji.
5. Poveži VM s virtualnim switchom koji si kreirao.
6. Kreiraj virtualni disk od 80–100 GB.
7. U instalacijskim opcijama odaberi Ubuntu Server ISO.
8. Završi čarobnjak i pokreni VM.

Ako instalacija ne počinje, provjeri ISO putanju i boot redoslijed u VM postavkama. Nemoj nasumično isključivati sigurnosne postavke hosta.

## 5. Instaliraj Ubuntu Server

1. Pokreni VM i prati instalacijski program Ubuntu Servera.
2. Odaberi jezik i raspored tastature.
3. Mrežu možeš postaviti na DHCP za prvi lab. Za stabilnu upotrebu preporučuje se DHCP reservation ili pažljivo konfigurirana statička adresa.
4. Odaberi disk koji pripada samo ovoj virtualnoj mašini i potvrdi particionisanje.
5. Kreiraj lokalnog administratora s jedinstvenom, snažnom lozinkom.
6. OpenSSH Server instaliraj samo ako ti je potreban; ograniči pristup na pouzdanu mrežu.
7. Završi instalaciju i restartuj VM. Ukloni ISO iz virtualnog DVD pogona ako se VM ponovo pokreće u instalacijski program.

Prijavi se u Ubuntu konzolu.

## 6. Ažuriraj Ubuntu i provjeri resurse

Pokreni:

```bash
sudo apt update
sudo apt full-upgrade -y
sudo reboot
```

Nakon ponovnog pokretanja provjeri sistem:

```bash
lsb_release -a
uname -m
nproc
free -h
df -h /
ip -br address
```

Očekivanja:
- OS je Ubuntu 24.04 LTS.
- Arhitektura je `x86_64`.
- Imaš najmanje 4 dodijeljena vCPU-a i oko 8 GiB RAM-a.
- Root filesystem ima dovoljno slobodnog prostora.
- Mrežni interfejs ima IP adresu.

Zapiši IP adresu. U narednim koracima koristi svoju adresu umjesto primjera.

## 7. Preuzmi i pokreni Wazuh installation assistant

Ovaj vodič cilja Wazuh 4.14.x. Provjeri zvaničnu dokumentaciju i izdanje prije izvođenja; nemoj slijepo kopirati komandu iz starog vodiča ako se promijenila podržana verzija.

Zvanični Quickstart za 4.14 koristi instalacijski assistant iz paketskog repozitorija:

```bash
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh
```

Prije pokretanja skripte, ako želiš dodatnu kontrolu, pregledaj sadržaj:

```bash
less wazuh-install.sh
```

Zatim pokreni all-in-one instalaciju:

```bash
sudo bash ./wazuh-install.sh -a
```

Skripta preuzima i konfiguriše centralne komponente. Instalacija može potrajati nekoliko minuta, zavisno od VM resursa i brzine mreže.

**Sigurnosna napomena:** izvršavanje preuzete skripte s `sudo` daje joj administratorske privilegije. Preuzimaj je samo sa zvaničnog Wazuh domena, provjeri izvor i prati aktuelnu službenu dokumentaciju. Nemoj koristiti nepoznate skripte s foruma ili iz komentara.

Ako skripta prijavi grešku, sačuvaj relevantan dio izlaza bez lozinki i tokena. Nemoj nasumično ponavljati instalaciju ili brisati direktorije dok ne utvrdiš uzrok.

## 8. Sačuvaj pristupne podatke

Na kraju uspješne instalacije assistant prikazuje sažetak, adresu dashboarda, korisnika i generisanu lozinku.

- Sačuvaj lozinku u password manageru.
- Ne stavljaj je u GitHub, screenshotove, video ili javne bilješke.
- Ne koristi istu lozinku kao na drugim sistemima.
- Ne šalji arhivu s tajnama drugim osobama.

Ako trebaš ponovo pročitati Wazuh generisane lozinke, službeni Quickstart opisuje arhivu `wazuh-install-files.tar` i datoteku `wazuh-passwords.txt`. Pristupi joj samo lokalno na VM-u i ne objavljuj sadržaj:

```bash
sudo tar -O -xvf wazuh-install-files.tar wazuh-install-files/wazuh-passwords.txt
```

Ako arhiva nije u trenutnom direktoriju, provjeri direktorij iz kojeg si pokrenuo installation assistant. Nemoj kopirati ovu datoteku u repozitorij.

## 9. Provjeri servise i mrežu

Provjeri stanje centralnih servisa:

```bash
sudo systemctl status wazuh-manager --no-pager
sudo systemctl status wazuh-indexer --no-pager
sudo systemctl status wazuh-dashboard --no-pager
```

Provjeri slušajuće portove:

```bash
sudo ss -lntup
```

Ako servis nije aktivan, provjeri njegove logove, npr.:

```bash
sudo journalctl -u wazuh-manager -n 100 --no-pager
sudo journalctl -u wazuh-indexer -n 100 --no-pager
sudo journalctl -u wazuh-dashboard -n 100 --no-pager
```

Tačan naziv servisa i log lokacije mogu zavisiti od verzije. Koristi zvanični troubleshooting vodič za poruku greške koju vidiš.

## 10. Otvori Wazuh dashboard

Na računaru koji ima mrežni pristup VM-u otvori:

```text
https://IP_ADRESA_TVOJE_VM
```

Primjer formata: `https://192.168.1.50` — ovo je samo primjer, nemoj koristiti adresu ako nije tvoja.

1. Unesi korisničko ime `admin`.
2. Unesi generisanu lozinku iz instalacijskog sažetka.
3. Prvi put može se pojaviti upozorenje za TLS certifikat koji nije izdat od javno pouzdanog CA-a. U laboratoriju je to moguće očekivano, ali provjeri da zaista pristupaš vlastitoj VM adresi. Za produkciju konfiguriraj pouzdan certifikat.
4. Nakon prijave provjeri da se dashboard otvara i da nema kritičnih grešaka.

Nemoj izlagati port 443 dashboarda javnom internetu. Ograniči pristup na pouzdane administrativne uređaje ili VPN.

## 11. Mrežni portovi — princip najmanjih privilegija

Za Wazuh 4.x uobičajeni portovi uključuju:
- `443/TCP` — dashboard web sučelje.
- `1514/TCP` — komunikacija agenata s managerom u uobičajenoj konfiguraciji.
- `1515/TCP` — agent enrollment u uobičajenoj konfiguraciji.
- `55000/TCP` — Wazuh API, koji ne treba izlagati nepouzdanim mrežama.

Provjeri portove i način rada za tačno izdanje i konfiguraciju koju koristiš. Ne otvaraj sve portove prema cijeloj mreži. Dozvoli samo ono što je potrebno iz odgovarajućih izvorišnih adresa. API i administrativni pristup ograniči na pouzdane uređaje.

## 12. Završna kontrolna lista

- [ ] Ubuntu je ažuriran.
- [ ] Wazuh instalacija završila bez greške.
- [ ] `wazuh-manager`, `wazuh-indexer` i `wazuh-dashboard` rade.
- [ ] Dashboard se otvara s administrativnog računara.
- [ ] Generisana lozinka je pohranjena u password manageru.
- [ ] Dashboard nije izložen internetu.
- [ ] Nema tajni, internih IP podataka ili osjetljivih screenshotova u Git repozitoriju.
- [ ] Zabilježena je verzija Wazuha i datum testiranja.

## 13. Problemi koji se često javljaju

### Dashboard se ne otvara
- Provjeri IP adresu s `ip -br address`.
- Provjeri `systemctl status wazuh-dashboard`.
- Provjeri mrežni switch, firewall i da klijent može doći do VM-a.
- Provjeri port 443 pomoću `ss -lntup`.

### VM je veoma spora
- Provjeri RAM, CPU i prostor na disku.
- Zaustavi druge nepotrebne VM-ove.
- Ne smanjuj memoriju ispod zahtjeva bez provjere posljedica.

### Instalacijska skripta ne uspije
- Pročitaj cijelu poruku greške.
- Provjeri podržani OS, verziju skripte i pristup internetu.
- Pregledaj službenu dokumentaciju za tačnu verziju.
- Nemoj objavljivati lozinke ili privatne podatke iz izlaza.

### Ne mogu pristupiti VM-u s hosta
- Provjeri tip virtualnog switcha.
- Internal i Private switch sami po sebi ne garantuju internet pristup.
- Provjeri IP adresu, rutu i firewall pravila.

## 14. Šta dalje?

Sljedeći vodič treba biti **Instalacija i povezivanje Wazuh agenta na Windows 11**. Nakon što agent bude povezan, možeš testirati prikupljanje događaja i napraviti prvu dokumentovanu detekciju.

## Izvori

- Wazuh Quickstart: https://documentation.wazuh.com/current/quickstart.html
- Wazuh Installation Guide: https://documentation.wazuh.com/current/installation-guide/index.html
- Wazuh Installation Assistant: https://github.com/wazuh/wazuh-installation-assistant
- Ubuntu Server documentation: https://ubuntu.com/server/docs
- Microsoft Hyper-V documentation: https://learn.microsoft.com/windows-server/virtualization/hyper-v/
