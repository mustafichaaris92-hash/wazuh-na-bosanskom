# Sigurnosna politika projekta

Ovaj projekat je edukativan. Svi testovi moraju se izvoditi u vlastitom labu ili uz izričito odobrenje vlasnika sistema.

## Nikad ne objavljuj

- Lozinke, API tokene, privatne ključeve ili certifikate.
- `wazuh-passwords.txt`, `.env` datoteke ili backup datoteke s tajnama.
- Stvarne korisničke podatke, e-mail adrese ili identifikatore zaposlenih.
- Internu topologiju, javne IP adrese, firewall pravila ili logove poslodavca bez pisanog odobrenja.
- Screenshotove koji prikazuju povjerljive informacije.

## Siguran rad u laboratoriju

- Koristi izolovan virtualni switch gdje je praktično.
- Nemoj izlagati dashboard ili Wazuh API direktno internetu.
- Koristi jedinstvene lozinke i password manager.
- Ograniči firewall pravila na potrebne izvorišne adrese i portove.
- Prije destruktivnih promjena napravi snapshot/backup VM-a.
- Testiraj detekcije samo na sistemima koje posjeduješ ili za koje imaš dozvolu.
- Za demonstracije napada koristi kontrolisane, bezopasne testne događaje i jasno ih označi.

## Prijava problema

Ako pronađeš sigurnosni problem u ovom repozitoriju:
1. Nemoj javno objavljivati exploitable detalje ili tajne.
2. Kontaktiraj održavaoca privatnim kanalom ako je dostupan.
3. Navedi pogođenu datoteku, korake za reprodukciju i očekivani uticaj.
4. Ako problem pripada Wazuh softveru, slijedi Wazuhov zvanični proces prijave ranjivosti.

Ova politika nije zamjena za pravila odgovornog otkrivanja ranjivosti dobavljača.
