# TkoJeTo — Instant Bio & Kontekst | Politika privatnosti (Privacy Policy)

**Datum stupanja na snagu / Effective Date:** 19. studenoga 2026.  
**Verzija ekstenzije / Extension Version:** 1.0.0

---

## Hrvatski (HR)

### O ekstenziji (Popratni tekst)
**TkoJeTo — Instant Bio & Kontekst** besplatna je *Zero-Backend* Chrome ekstenzija namijenjena čitateljima informativnih portala (primarno Ex-Yu regije). Tijekom čitanja članaka omogućuje trenutačni uvid u biografiju, funkciju, akademski profil i novije vijesti o javnim osobama — jednim klikom na prepoznato ime ili ručnim označavanjem imena mišem, uz automatsku Ex-Yu morfološku normalizaciju (svođenje padeža i dvostrukih prezimena na nominativ).

---

### Politika privatnosti

Ekstenzija **TkoJeTo** dizajnirana je prema načelu maksimalne privatnosti (**Privacy-by-Design**) i radi u potpunosti bez vlastitog poslužitelja (*Zero-Backend*).

#### 1. Koje podatke prikupljamo?
**Ne prikupljamo, ne pohranjujemo na vanjskim poslužiteljima i ne pratimo nikakve osobne podatke korisnika.** Ekstenzija:
- **Ne prikuplja** povijest pregledavanja (*browsing history*), URL-ove članaka koje čitate ni sadržaj stranica.
- **Ne koristi** kolačiće trećih strana (*tracking cookies*), Google Analytics ni ikakve oglasne ili analitičke SDK-ove.
- **Ne zahtijeva** korisnički račun, registraciju niti unos osobnih podataka (ime, e-mail, IP adresa).

#### 2. Kako ekstenzija obrađuje tekst na stranici?
- **Lokalno prepoznavanje imena:** Skripta za prepoznavanje imena u člancima (`content.js`) izvršava se **isključivo lokalno u vašem pregledniku**. Cijeli tekst članka nikada se ne šalje izvan vašeg uređaja.
- **Slanje pojedinačnog upita na vaš zahtjev:** Tek kada vi izravno kliknete na podcrtano ime ili označite ime mišem i zatražite prikaz kartice, pozadinski servis ekstenzije (`background.js`) šalje **isključivo normalizirano ime i prezime te osobe** javnim servisima kako bi dohvatio enciklopedijski sažetak i javni kontekst.
- **Zaštita privatnosti pri učitavanju slika (`no-referrer`):** Slike profila javnih osoba unutar kartice učitavaju se s atributom `referrerPolicy="no-referrer"`, čime se sprječava da vanjski poslužitelji saznaju adresu portala ili članka koji čitate.

#### 3. Vanjski javni API izvori koji primaju upit (samo ime osobe)
Kada zatražite podatke o osobi, pozadinski servis šalje upit s imenom osobe isključivo sljedećim javnim izvorima putem HTTPS-a:
1. **Wikipedia** (`*.wikipedia.org`) — sažeci i pretraga enciklopedijskih članaka.
2. **Wikidata** (`*.wikidata.org`) — javni strukturirani podaci (datum rođenja, uloge, organizacije, obrazovanje).
3. **OpenAlex API** (`api.openalex.org`) — javni akademski i znanstveni profili istraživača.
4. **DuckDuckGo Instant Answer API** (`api.duckduckgo.com`) — rezervni javni enciklopedijski sažeci.
5. **Google News RSS** (`news.google.com`) — javni naslovi novijih vijesti vezanih uz traženu osobu.
6. **Google Translate** (`translate.googleapis.com`) — isključivo za prijevod javnih biografskih tekstova sa stranih jezika na odabrani jezik prikaza korisnika.

#### 4. Dozvole ekstenzije (*Permissions*)
- `storage`: Koristi se isključivo lokalno na vašem uređaju (`chrome.storage.local` i `chrome.storage.session`) za spremanje vaših postavki (primarni jezik, prozirnost kartice, isključene domene) i privremene 24-satne predmemorije (*cache*, ograničene na najviše 300 zapisa) radi bržeg rada i manjeg broja mrežnih upita.
- `activeTab`: Koristi se isključivo u trenutku kada otvorite skočni prozor postavki ekstenzije, kako bi vam se mogao ponuditi brzi gumb za isključivanje ili ponovno uključivanje ekstenzije na trenutačnoj domeni (npr. `Isključi na: portal.hr`).

#### 5. Kontrola nad podacima i isključenja
- Ekstenzija po zadanom automatski preskače osjetljive web-aplikacije (npr. `mail.google.com`, `docs.google.com`, `drive.google.com`, `outlook.live.com`, `github.com`, `web.whatsapp.com` itd.).
- U postavkama ekstenzije u svakom trenutku možete dodati vlastite domene na popis isključenih stranica, obrisati cjelokupnu 24-satnu predmemoriju jednim klikom ili ukloniti ekstenziju (čime se svi lokalno spremljeni podaci odmah brišu).

---

## English (EN)

### Extension Overview
**TkoJeTo — Instant Bio & Kontekst** is a free, zero-backend Chrome extension built for readers of news portals (primarily across the Ex-Yu region). It provides an instant bio card, structured facts, academic context, and recent news headlines for public figures when clicking highlighted names or selecting text, featuring morphological normalization for South Slavic cases and double surnames.

---

### Privacy Policy

**TkoJeTo** is built on Privacy-by-Design principles and operates without any proprietary backend server.

#### 1. Data Collection
**We do not collect, transmit to developer servers, sell, or track any personal or browsing data.** Specifically:
- We **do not** collect browsing history, visited URLs, page contents, or user identifiers.
- We **do not** use third-party analytics, telemetry, tracking cookies, or advertising SDKs.
- No user account or registration is required.

#### 2. Local Processing & Query Transmission
- **On-device detection:** Automatic person-name recognition (`content.js`) runs **100% locally inside your browser**. Full webpage text never leaves your device.
- **User-initiated lookup only:** Only when you click a recognized name or manually trigger a lookup for a highlighted selection (2–5 words) does the background service worker (`background.js`) send **only the normalized person name query** to public APIs to retrieve biographical summaries.
- **Image referrer protection:** Public profile thumbnails rendered inside the popup card enforce `referrerPolicy="no-referrer"` so external image hosts do not receive the URL of the webpage you are reading.

#### 3. Third-Party Public Read-Only APIs Queried
When you initiate a person lookup, only the queried person's name (and when translating foreign summaries, the public snippet text) is sent over HTTPS to:
- **Wikipedia** (`https://*.wikipedia.org/*`)
- **Wikidata** (`https://*.wikidata.org/*`)
- **OpenAlex API** (`https://api.openalex.org/*`)
- **DuckDuckGo Instant Answer API** (`https://api.duckduckgo.com/*`)
- **Google News RSS** (`https://news.google.com/*`)
- **Google Translate** (`https://translate.googleapis.com/*`)

#### 4. Extension Permissions Justification
- `storage`: Used strictly locally (`chrome.storage.local` and `chrome.storage.session`) to persist user preferences (language, background opacity slider, excluded domains list) and a bounded 24-hour lookup cache (capped at 300 entries).
- `activeTab`: Accessed solely when opening the extension settings popup in order to read the current tab's hostname for the 1-click *"Exclude / Re-enable on this domain"* control.

#### 5. Data Sharing & Chrome Web Store Limited Use Compliance
- User data is never sold, rented, or shared with advertisers, data brokers, or unrelated third parties.
- Sensitive productivity/messaging web apps (e.g., Gmail, Google Docs, Outlook, GitHub, Slack, WhatsApp Web) are excluded by default, and users can add or remove any custom domain in settings.
- Users may clear all cached lookups at any time in settings or uninstall the extension to immediately delete all locally stored preferences and cache entries.

---

### Kontakt / Support & Contact
Za pitanja vezana uz privatnost ili prijavu problema otvorite zahtjev na javnom GitHub repozitoriju:  
For privacy inquiries or support requests, please open an issue on the public GitHub repository:  
- [https://github.com/vugy0212/tko-je-to-privacy/issues](https://github.com/vugy0212/tko-je-to-privacy/issues)
