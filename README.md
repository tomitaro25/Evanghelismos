# Ευαγγελισμός — Flashcards Ελληνικά ⇄ Română (Buna Vestire)

Aplicație dedicată părintelui Daniel.

Aplicație de exersat vocabular grec-român, sub formă de PWA (Progressive Web App) instalabilă pe telefon.

**⚠️ Versiune de test (v3)** — vocabularul conține momentan 794 de cuvinte (650 A1 + 144 început de A2), construite din rangurile de frecvență ~1-2500 ale limbii grecești moderne. Nivelurile B1/B2 nu sunt încă populate. Modulele „Antonime & Sinonime" și „Conjugare verbe" (prezente în aplicația soră de germană) nu sunt încă implementate — sunt planificate pentru o fază separată, cu date construite specific pentru greacă.

## Istoric versiuni

- **v4** — Corectat layout-ul barei de sus pe telefoane Android: numele lung al aplicației (Ευαγγελισμός) împingea butonul de Setări (⚙) pe un rând nou, micșorând spațiul aplicației. Numele se trunchiază acum cu „..." dacă nu încape, iar pe ecrane înguste (sub 420px) controalele de zoom din bara de sus se ascund (rămân identic disponibile în Setări) — mic/AI/setări rămân mereu pe același rând.
- **v3** — Vocabular extins: de la 178 la 794 de cuvinte (650 A1 + 144 început de A2), lematizate și traduse manual din rangurile de frecvență 400–2500. Adăugată funcția de detectare a vocii grecești lipsă din sistem, cu ghidare specifică per platformă (Windows/Android — deschidere directă a ecranului de setări; iOS/macOS — instrucțiuni text, din limitări de browser).
- **v2** — Redenumire completă: Ευαγγελισμός (Buna Vestire), dedicată părintelui Daniel. Corectate bug-uri de portare rămase (clasele CSS de gen nu se mapau corect la ο/η/το, referințe reziduale „DE"/„7000 de cuvinte" moștenite din aplicația germană, în secțiunea de Ajutor).
- **v1** — Prima versiune funcțională, portată din arhitectura Karteikarten (germană): motor de flashcards, căutare/adăugare cuvinte, backup, modul AI (Claude) adaptat pentru RO↔EL, iconițe cu steag elen. Vocabular de test: 178 cuvinte A1, lematizate și traduse manual.

## Ce conține

- `index.html` — aplicația
- `vocab-data.js` — baza de vocabular (A1: 650 cuvinte, A2: 144 cuvinte — versiune de test, în extindere)
- `manifest.json` — configurare PWA (nume, iconițe, mod de afișare)
- `sw.js` — service worker (funcționare offline)
- `icon-192.png`, `icon-512.png` (+ variante maskable) — iconițele aplicației, cu accent pe steagul elen (albastru-alb)

## Funcționalități

Aceleași funcționalități de bază ca aplicația soră **Karteikarten** (germană) și **La Boîte de Fiches** (franceză), adaptate pentru greacă:

- Traducere greacă ⇄ română, grilă cu 4 variante de răspuns, cu distractori din aceeași categorie gramaticală (substantiv/verb/expresie/cuvânt funcțional) — clasificarea verbelor grecești se bazează pe terminațiile de persoana I singular prezent (-ω/-ώ/-μαι), fără infinitiv (greaca modernă nu are infinitiv — convenția de dicționar/școală folosește persoana I singular)
- Gen gramatical afișat cu articol: **ο** (masculin), **η** (feminin), **το** (neutru)
- Selector de direcție: EL→RO, RO→EL, sau ambele amestecat
- Mod de exersare „inteligent" (repetiție spațiată bazată pe istoricul de răspunsuri) sau complet aleator
- Pronunție audio a cuvintelor grecești (Web Speech API, `el-GR`), cu alegere de voce
- Link direct către [Glosbe](https://ro.glosbe.com/el/ro) pentru fiecare cuvânt grecesc, ca sursă suplimentară de verificare (dict.cc nu are pereche directă EL-RO)
- Buton „Sari peste", căutare de cuvinte (scrisă + vocală, cu recunoașterea și eliminarea automată a articolelor grecești), adăugare manuală de cuvinte lipsă, backup complet, prompt de instalare — toate identice funcțional cu aplicația germană
- **🤖 AI (Claude) — traducere liberă** — adaptată complet pentru perechea română-greacă, inclusiv reconstrucția automată a accentuării grecești (τόνος) pierdute la dictarea vocală (echivalentul grecesc al problemei cratimelor din română)
- Preferințele și statisticile se salvează local, în browser, per dispozitiv

## Ce lipsește față de aplicația germană (intenționat, fază separată)

- Nivelurile B1/B2/Suplimentar (A1 și început de A2 populate momentan)
- Modulul „Antonime & Sinonime"
- Modulul „Conjugare verbe"
- Vocabular de specialitate (echivalentul „Îngrijire" din aplicația germană)

## Instalare pe telefon

1. Deschide link-ul GitHub Pages al acestui repository, în Chrome (Android) sau Safari (iOS)
2. Din meniul browserului, alege "Adaugă la ecranul principal" / "Instalează aplicația"
3. Aplicația apare cu propria iconiță și funcționează parțial offline

## Surse și atribuiri

- **Selecția cuvintelor A1** e construită din rangul de frecvență reală de utilizare a limbii grecești moderne, pe baza listei [hermitdave/FrequencyWords](https://github.com/hermitdave/FrequencyWords) (`content/2016/el/el_50k.txt`, derivată din corpus OpenSubtitles), licență **MIT**.
- Spre deosebire de aplicația franceză (lematizată programatic cu spaCy `fr_core_news_sm`), toate cele 794 de cuvinte au fost **lematizate și verificate integral manual** — formele flexionate din topul de frecvență brut (ex. toate formele lui „a avea": έχω/έχεις/έχει/είχα...) au fost reduse manual la lema corectă, iar numele proprii și argoul vulgar din corpusul de subtitrări au fost excluse. Loturile viitoare vor evalua dacă merită folosit spaCy `el_core_news_sm` (cunoscut cu probleme de nedeterminism la lematizare, per issue-uri publice) sau dacă verificarea manuală rămâne mai eficientă la acest volum.
- Traducerile în limba română sunt muncă originală.
- Genul gramatical (ο/η/το) e marcat manual, per cuvânt.
- Verbele apar la persoana I singular, prezent, activ (convenția standard grecească de dicționar — greaca modernă nu are infinitiv).
- Acest proiect e o resursă personală de studiu, nu revendică nicio afiliere cu hermitdave, Glosbe, Anthropic sau alte instituții/persoane menționate.

## Confidențialitate

Aplicația nu colectează, nu transmite și nu stochează nicio dată pe niciun server. Tot ce ține de progres (statistici, preferințe) rămâne local, în browser-ul dispozitivului tău. Singurele conexiuni externe sunt: Google Fonts (fonturi), Glosbe (doar dacă apeși linkul respectiv) și motorul de sinteză vocală al telefonului. **Excepție:** funcția de căutare vocală (🎤) trimite sunetul către serverele browserului (ex. Google, pentru Chrome) ca să fie transformat în text — o limitare a tehnologiei din browser, nu ceva controlat de noi. Nu apare deloc pe iOS/Safari (Apple nu oferă acest API acolo).

## Licență

Codul aplicației (`index.html`, `sw.js`, `manifest.json`) e disponibil liber pentru refolosire și modificare personală. Vocabularul urmează atribuirile de mai sus (MIT pentru selecția de frecvență; traducerile românești sunt libere de folosit, fără garanții).

## Disclaimer

Vocabularul și traducerile pot conține ocazional imprecizii; verifică independent (ex. Glosbe, linkul din aplicație) orice cuvânt de care nu ești sigur. Aplicația nu oferă consultanță de niciun fel — e strict un instrument de exersare, oferit "ca atare", fără nicio garanție.

## Donații / susținere

Aplicația **nu are** (deocamdată) niciun buton de donații și nu e monetizată în niciun fel. E un proiect personal, distribuit liber.
