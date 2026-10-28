# YouTube plan: Instalacija Wazuha na Hyper-V (bez glasa)

## Format
- Snimak ekrana bez naracije
- Tekstualni natpisi na bosanskom jeziku
- Engleski stručni termini ostaju u zagradama gdje je korisno
- Ciljana dužina: 8–15 minuta
- Snimanje: OBS Studio
- Montaža: bilo koji editor koji podržava tekstualne natpise

## Prije snimanja

- Prođi cijeli vodič od početka do kraja.
- Napravi Hyper-V snapshot.
- Zatvori privatne dokumente, e-mail, password manager i druge osjetljive prozore.
- Koristi testnu VM i testne kredencijale.
- Isključi obavijesti operativnog sistema.
- Provjeri da se na ekranu ne vide stvarni interni podaci.
- Ne prikazuj generisanu admin lozinku. Ako se pojavi, zaustavi snimanje i ponovi taj dio.

## Storyboard

| Vrijeme | Snimak | Tekst na ekranu |
|---|---|---|
| 00:00–00:20 | Naslovna kartica | „Instalacija Wazuha na Hyper-V — vodič na bosanskom“ |
| 00:20–00:50 | Hyper-V Manager | „Cilj: edukativni Wazuh lab na Ubuntu Serveru 24.04 LTS“ |
| 00:50–01:30 | Postavke VM-a | „Početno: 4 vCPU, 8–12 GiB RAM, 80–100 GB disk“ |
| 01:30–03:30 | Ubuntu instalacija | „Instaliraj Ubuntu Server i provjeri mrežnu adresu“ |
| 03:30–04:30 | Terminal | „Ažuriraj sistem: apt update i full-upgrade“ |
| 04:30–06:30 | Terminal | „Preuzmi zvanični Wazuh 4.14 installation assistant“ |
| 06:30–08:30 | Terminal, instalacija | „Pokreni all-in-one instalaciju; ne prikazuj lozinke“ |
| 08:30–10:00 | Servisi i dashboard | „Provjeri servise i otvori dashboard preko privatne IP adrese“ |
| 10:00–10:30 | GitHub README | „Kompletan vodič i izvori nalaze se na GitHubu“ |

## Pravila za natpise

- Jedna ideja po ekranu.
- Drži tekst kratak i dovoljno velik.
- Ne prikazuj komande brže nego što ih gledalac može pročitati.
- Za duže komande prikaži ih u posebnom kadru.
- Dodaj natpis „Primjer IP adrese — zamijeni svojom adresom“ gdje je potrebno.
- Nemoj tvrditi da je instalacija uspješna ako je nisi provjerio.

## Opis videa — nacrt

U ovom videu prikazujem instalaciju Wazuha na Hyper-V laboratorijskoj virtualnoj mašini s Ubuntu Serverom 24.04 LTS. Video nema naraciju; svi ključni koraci objašnjeni su tekstom na ekranu.

Kompletan vodič na bosanskom jeziku: [DODAJ LINK NA GITHUB VODIČ]

Zvanična dokumentacija:
- https://documentation.wazuh.com/current/quickstart.html
- https://documentation.wazuh.com/current/installation-guide/index.html

Napomena: edukativni lab. Ne izlažite dashboard ili API internetu. Provjerite zvaničnu dokumentaciju prije produkcijske upotrebe.

#Wazuh #Cybersecurity #SIEM #HyperV #Bosanski
