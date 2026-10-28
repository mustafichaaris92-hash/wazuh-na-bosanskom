# Wazuh na Bosanskom

Praktični, nezavisni edukativni projekat za učenje Wazuha na bosanskom jeziku, uz zadržavanje ključnih engleskih stručnih termina.

> **Status:** edukativni projekat u razvoju  
> **Prvi vodič:** Instalacija Wazuha na Hyper-V koristeći Ubuntu Server 24.04 LTS  
> **Publika:** IT administratori, studenti i početnici u cybersecurityju iz Bosne i Hercegovine i regije

## Ciljevi projekta

- Objasniti Wazuh i povezane sigurnosne koncepte na bosanskom jeziku.
- Objavljivati praktične, ponovljive laboratorijske vježbe.
- Povezati svaki vodič s originalnom dokumentacijom i navesti testirane verzije.
- Razvijati portfolio iz SIEM-a, endpoint monitoringa, detekcije i incident responsea.
- Objavljivati kratke YouTube demonstracije snimljene s ekrana, bez glasa.

## Sadržaj

- [`docs/01-instalacija-wazuha-hyper-v.md`](docs/01-instalacija-wazuha-hyper-v.md) — prvi vodič
- [`docs/security-policy.md`](docs/security-policy.md) — pravila za sigurnost i prijavu problema
- [`docs/licensing-and-attribution.md`](docs/licensing-and-attribution.md) — licenciranje i atribucija
- [`youtube/01-instalacija-wazuha-hyper-v.md`](youtube/01-instalacija-wazuha-hyper-v.md) — plan prvog videa
- [`CONTRIBUTING.md`](CONTRIBUTING.md) — pravila doprinosa
- [`DISCLAIMER.md`](DISCLAIMER.md) — odricanje od odgovornosti i nezavisnost projekta

## Početak rada

1. Napravi novi javni GitHub repozitorij pod nazivom `wazuh-na-bosanskom`.
2. Dodaj datoteke iz ovog projekta.
3. Pročitaj prvi vodič i provjeri da li tvoj Hyper-V host ima dovoljno RAM-a i prostora na disku.
4. Izvedi instalaciju u izolovanom laboratoriju.
5. Zabilježi verzije, rezultate i eventualne razlike u odnosu na vodič.
6. Tek nakon uspješnog testiranja objavi vodič kao provjeren.

## Tehnički principi

- Svaki vodič mora navesti testirane verzije, datum provjere i pretpostavke.
- Nikad ne objavljuj lozinke, tokene, privatne ključeve, certifikate, interne logove ili podatke poslodavca.
- Koristi vlastite screenshotove iz laboratorija i ukloni osjetljive podatke.
- Komande koje mijenjaju sistem objasni prije nego što ih preporučiš.
- Ne predstavljaj ovaj projekat kao zvaničnu Wazuh dokumentaciju niti sugeriši da ga Wazuh podržava.
- Nemoj kopirati ili doslovno prevoditi tuđu dokumentaciju bez provjere licence i uslova atribucije.

## Plan razvoja

### Faza 1 — Osnove
- [ ] Instalacija Wazuha na Hyper-V
- [ ] Prvo prijavljivanje na dashboard
- [ ] Dodavanje Windows agenta
- [ ] Provjera da agent šalje događaje

### Faza 2 — Logovi i detekcija
- [ ] Uvod u alerts, rules i decoders
- [ ] File Integrity Monitoring (FIM)
- [ ] Windows Event Logs
- [ ] Linux logovi i SSH autentikacija

### Faza 3 — Integracije
- [ ] FortiGate Syslog u izolovanom labu
- [ ] Vulnerability Detection
- [ ] Security Configuration Assessment (SCA)
- [ ] Testiranje i dokumentovanje false positive rezultata

### Faza 4 — Portfolio
- [ ] Pet demonstracija s ponovljivim koracima
- [ ] YouTube snimci ekrana bez naracije
- [ ] Kratke tehničke objave na LinkedInu
- [ ] Pregled licenci, sigurnosti i kvaliteta dokumentacije prije svakog izdanja

## Zvanični izvori

- Wazuh Quickstart: https://documentation.wazuh.com/current/quickstart.html
- Wazuh Installation Guide: https://documentation.wazuh.com/current/installation-guide/index.html
- Wazuh Documentation: https://documentation.wazuh.com/current/index.html
- Wazuh Installation Assistant: https://github.com/wazuh/wazuh-installation-assistant
- GitHub dokumentacija za licence: https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository

## Licenca ovog repozitorija

Prije dodavanja `LICENSE` datoteke odaberi licencu koja odgovara vlastitim tekstovima, skriptama i drugim prilozima. Pogledaj `docs/licensing-and-attribution.md`. Nemoj pretpostaviti da licenca Wazuh softvera automatski određuje licencu svih materijala u ovom repozitoriju.
