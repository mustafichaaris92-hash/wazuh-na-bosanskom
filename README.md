# wazuh-na-bosanskom

**Praktični SIEM i XDR vodiči na bosanskom jeziku, uz korištenje industrijskih engleskih termina.**

### O projektu

**Wazuh na Bosanskom** je edukativni *open-source* projekat namijenjen svima koji žele savladati implementaciju, konfiguraciju i napredno korištenje Wazuh platforme za sigurnosni nadzor i detekciju prijetnji.

Cilj projekta je demistificirati *enterprise cybersecurity* i približiti Wazuh lokalnoj IT zajednici kroz praktične, *step-by-step* vodiče bazirane na realnim scenarijima. Materijali su napisani na bosanskom jeziku, uz pažljivo zadržavanje originalnih engleskih stručnih termina kako bi se olakšalo snalaženje u zvaničnoj dokumentaciji i svakodnevnom radu u produkciji.

### Šta ćemo sve pokriti? 🚀

Umjesto suhoparne teorije, fokusiramo se na maksimalnu iskoristivost Wazuha i njegovu primjenu u stvarnim mrežnim okruženjima. Kroz projekat ćeš naučiti:

* **Arhitektura i Setup:** Instalacija i optimizacija Wazuha na Hyper-V okruženju (pravilan odabir resursa: CPU, RAM, Disk).
* **Deployment Agenata (Wazuh Agents):** Od ručne instalacije do automatiziranog *deploymenta* putem skripti i Active Directory GPO-a (Group Policy Object) za *enterprise* okruženja.
* **Mrežna integracija i Log Logging:** Uvezivanje mrežnog perimetra – slanje logova i sigurnosnih događaja sa **FortiGate** firewall-a direktno na Wazuh.
* **Proaktivna zaštita (Active Response):** Konfiguracija Wazuha da ne bude samo pasivni posmatrač, već da automatski blokira napade i izoluje kompromitovane uređaje u stvarnom vremenu.
* **Moderni Alerting:** Integracija sa komunikacijskim platformama – slanje kritičnih *alerta* (Security Events and Alerts) direktno na **Discord** kanale.
* **Analitika i optimizacija:** Praćenje resursa, *threat hunting* i podešavanje sistema da radi besprijekorno pod opterećenjem.

### Roadmap vodiča 🗺️

Vodiči će se dodavati postepeno, tek nakon što svaka konfiguracija prođe rigorozno testiranje u lab okruženju.

1. **Instalacija Wazuha na Hyper-V** — Priprema virtualne mašine i potpuni setup platforme.
2. **Windows Agent Deployment** — Povezivanje Windows računara i servera sa Wazuhom.
3. **Masovna instalacija (GPO & Skripte)** — Automatizacija instalacije agenata kroz Active Directory.
4. **FortiGate Integracija** — Prosljeđivanje i parsiranje logova sa FortiGate firewall-a.
5. **Active Response** — Postavljanje automatskih skripti za blokiranje detektovanih napada.
6. **Discord Alerting** — Konfiguracija webhookova za obavještenja u realnom vremenu.

### Kome je projekat namijenjen? 🎯

* **Sistem i mrežnim administratorima** koji žele implementirati moćan SIEM/XDR alat u svoju infrastrukturu.
* **IT entuzijastima i početnicima** koji žele izgraditi čvrste temelje iz cyber sigurnosti.
* **Studentima** u potrazi za praktičnim, *hands-on* iskustvom koje se traži na tržištu rada.
* Svima koji žele podići sigurnosne standarde u svom okruženju (uključujući usklađivanje sa normama poput ISO 27001).

### Napomena i odricanje od odgovornosti ⚠️

Ovaj projekat je nezavisna inicijativa zajednice (community project). Nije službeni proizvod niti je direktno povezan s kompanijom Wazuh, Inc.
Sve konfiguracije su kreirane u dobroj namjeri za edukaciju. Prije implementacije u produkcijsko okruženje, **obavezno ih testiraj**, prilagodi vlastitoj infrastrukturi i slijedi interne sigurnosne preporuke.

### Licenca i izvori 📄

Wazuh je fantastična platforma otvorenog koda. Svi nazivi, logotipi i originalna dokumentacija pripadaju njihovim odgovarajućim vlasnicima. Za dublju tehničku referencu, uvijek konsultuj službenu Wazuh dokumentaciju(https://documentation.wazuh.com/).

---

**Jezik:** Bosanski (uz engleske stručne termine) | **Svrha:** Edukacija, praktična primjena i jačanje IT zajednice.

---
