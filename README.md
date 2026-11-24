# WhoIsIt — TkoJeTo (Instant Bio & Context)

[![Chrome Web Store](https://img.shields.io/badge/Chrome_Web_Store-Available-blue?logo=googlechrome&logoColor=white)](https://chromewebstore.google.com/detail/whoisit-%E2%80%94-tkojeto-instant/ehachdpjcahdlebkdmfpnagjchaigokk)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Chrome ekstenzija (**Manifest V3**, čisti Vanilla JS bez vanjskih ovisnosti i build koraka) koja tijekom čitanja portala pruža trenutni uvid u biografiju, ulogu i aktualni kontekst javnih osoba — klikom na automatski podcrtano ime ili označavanjem teksta mišem.

> 🚀 **Instalirajte izravno s [Chrome Web Store](https://chromewebstore.google.com/detail/whoisit-%E2%80%94-tkojeto-instant/ehachdpjcahdlebkdmfpnagjchaigokk)**!

## Glavne značajke

- **Automatsko prepoznavanje i podcrtavanje imena** u člancima (uključujući Ex-Yu padeže, inicijale s točkom i bez točke, imena s crticom, portalne tipfelere poput `llija` → `Ilija` te imena unutar portalnih `<a>` linkova uz presretanje navigacije), uz **pretragu jednoriječnih prezimena i nadimaka na zahtjev** (`Alt + označavanje/dvoklik`).
- **Ex-Yu morfološka normalizacija** — automatsko svođenje kosih padeža (*s Andrejem Plenkovićem*, *Ane Brnabić*, *Iliji Srdanoviću*, *Lidiju Vukićević*) i uklanjanje titula (`dr. sc.`, `prof.`, `gen.`) na nominativ.
- **Lokalno kontekstualno rangiranje imenjaka (*Smart Disambiguation*)** — lokalna analiza šire teme okolnog odlomka (*sport, politika, film, glazba, znanost, pravo, biznis, književnost, vojska*) u pregledniku postavlja najvjerojatnijeg imenjaka na prvi tab (tekst članka nikad ne napušta uređaj).
- **Kaskadni besplatni izvori podataka (Zero-Backend, bez API ključeva):**
  1. **Wikipedia** (`hr`, `sr` latinica/ćirilica, `bs`, `en`) + automatski prijevod stranih sažetaka na odabrani jezik
  2. **Wikidata** (strukturirani podaci: rođenje/dob, mjesto, dužnost, stranka, zanimanje, obrazovanje, državljanstvo)
  3. **OpenAlex API** (akademski i znanstveni profili, institucije, broj radova, citati i h-indeks)
  4. **DuckDuckGo Instant Answer API** (dodatni sažeci za međunarodne osobe)
  5. **Google Vijesti RSS** (*"Nedavno u vijestima"* — zadnja 3 novinska naslova)
- **Shadow DOM izolirani UI, teme i oznaka godina života** — izbor **Tamne / Svijetle / Automatske (Sustav)** teme kartice i popupa, pametno bočno pozicioniranje, oznaka godina života za povijesne i preminule osobe (`1856–1943`), proširivi prikaz (**Pročitaj još ▾**), brzi fallback linkovi na Google/Wikipedia pretragu te podnožje s klikabilnim izvorom, licencom (`CC BY-SA 4.0` / `CC0 1.0`) i ogradom od odgovornosti.
- **Povlačenje, višestruko prikvačivanje uz tekst i tipkovnička navigacija** — karticu možete povući za zaglavlje, prikvačiti je ikonom **📌** na točno mjesto u dokumentu da se skrola sa stranicom (do **4 prikvačene kartice** istovremeno uz 1 aktivnu plutajuću, zaštitu od preklapanja i duplikata) te mijenjati tabove imenjaka strelicama `←` / `→`.
- **Službena i18n lokalizacija i lokalizirani datumi** — `_locales/` podrška za engleski, hrvatski i srpski u trgovinama (`en`, `hr`, `sr`), automatsko prepoznavanje jezika preglednika pri prvoj instalaciji te formatiranje datuma prema odabranom jeziku.
- **Provjera licenci fotografija (Wikimedia Commons)** — prikazuju se isključivo fotografije s Wikimedia Commonsa s potvrđenom slobodnom licencom uz navođenje autora, licence i poveznice na datoteku; lokalne *fair use* i neprovjerene slike automatski se filtriraju (prikazuju se inicijali).
- **Podešavanje prozirnosti i Peek-through** — klizač u postavkama (60% – 100%) s modernim *frosted glass* (backdrop-filter) efektom koji zadržava 100% oštrinu slova unutar kartice. Dok je prozor otvoren, držanje tipke **Alt** ili ikone oka 👁️ u zaglavlju privremeno ga čini prozirnim radi brzog čitanja teksta portala ispod njega.
- **Upravljanje isključenim stranicama i servisima** — brzi gumb jednim klikom za isključivanje/uključivanje aktivne domene, prilagodljivi popis isključenih domena i servisa u postavkama te zadano izuzeće za web-aplikacije (Gmail, Google Docs/Drive, GitHub, Figma, Slack itd.).
- **Predmemoriranje, privatnost i performanse** — 24-satno predmemoriranje u memoriji i `chrome.storage.local` s automatskim čišćenjem isteklih zapisa (TTL) i LRU ograničenjem na 300 unosa, `referrerPolicy = 'no-referrer'` na slikama avatara, inkrementalno `MutationObserver` skeniranje novododanih elemenata te podrška za tipkovnicu (`Tab`, `Enter`/`Space`) na podcrtanim imenima.

## Struktura projekta

- `manifest.json` — Manifest V3 konfiguracija, `default_locale`, dozvole i `host_permissions`
- `_locales/` — Službene lokalizacije trgovine i preglednika (`en`, `hr`, `sr`)
- `background.js` — Service Worker (normalizacija, detekcija jezika, 24h cache s automatskim čišćenjem, kaskadni dohvat, provjera Commons licenci i prijevod)
- `content.js` — Detekcija selekcije, inkrementalno automatsko podcrtavanje imena i Shadow DOM UI s podnožjem izvora/licenci i brzim fallback tražilicama
- `popup.html` & `popup.js` — Postavke (uključeno/isključeno, primarni jezik, fallback jezici, način prikaza, tema tamna/svijetla/sustav, automatsko podcrtavanje, klizač prozirnosti, isključene stranice/servisi, uputa, izvori/licence/ograda i brisanje predmemorije)
- `tests/extension.test.js` — Unit testovi (`node --test tests/extension.test.js`)
- `icons/` — PNG ikone (`16x16`, `48x48`, `128x128`)
- `ROADMAP.md` — Plan daljnjeg razvoja po fazama
- `LICENSE` — MIT licenca izvornog koda

## Izvori, licence i ograda od odgovornosti

- **Tekst i sažeci:** Biografski tekstovi preuzimaju se s Wikipedije (`wikipedia.org`) pod licencom `CC BY-SA 4.0` (uz mogući strojni prijevod putem Google Translatea).
- **Fotografije:** Prikazuju se isključivo slobodno licencirane fotografije s Wikimedia Commonsa uz navođenje autora, licence i poveznice na stranicu datoteke; lokalne *fair use* slike i slike bez jasne slobodne licence automatski se preskaču.
- **Ostali podaci:** Wikidata (`CC0 1.0`), OpenAlex (`CC0 1.0`), DuckDuckGo Instant Answer API i Google Vijesti RSS (vlasništvo izvornih nakladnika).
- **Ograda:** Podaci se prikazuju izravno iz javnih izvora bez neovisne provjere — mogu biti nepotpuni, zastarjeli ili povremeno odgovarati pogrešnoj osobi (osobito kod istih imena i prezimena). Projekt nije povezan sa Zakladom Wikimedia niti ga ona podržava.

## Instalacija u Google Chrome

### 1. Službena instalacija (Preporučeno)
Jednostavno posjetite **[WhoIsIt — TkoJeTo na Chrome Web Store](https://chromewebstore.google.com/detail/whoisit-%E2%80%94-tkojeto-instant/ehachdpjcahdlebkdmfpnagjchaigokk)** i kliknite **"Add to Chrome"** (*Dodaj u Chrome*).

### 2. Ručna instalacija iz izvornog koda (za developere)
1. Klonirajte ili preuzmite ovaj repozitorij.
2. Otvorite `chrome://extensions` u pregledniku.
3. Uključite **Developer mode** u gornjem desnom kutu.
4. Kliknite **Load unpacked** i odaberite mapu ovog repozitorija.
