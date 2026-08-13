# Ευαγγελισμός — Flashcards Ελληνικά ⇄ Română (Buna Vestire)

Aplicație dedicată părintelui Daniel.

Aplicație de exersat vocabular grec-român, sub formă de PWA (Progressive Web App) instalabilă pe telefon.

**⚠️ Versiune de test (v10)** — vocabularul conține 1858 de cuvinte: A1 (650), A2 (608) și B1 (600) complete. Modulul „Antonime & Sinonime" e implementat (59 perechi antonime + 20 perechi sinonime). Nivelul B2 și modulul „Conjugare verbe" (prezent în aplicația soră de germană) rămân pentru o fază viitoare.

## Istoric versiuni

- **v12** — Corectată gramatical eticheta implicită de pe carduri (modul obișnuit de traducere): „Traduce" nu era o formă corectă de instrucțiune izolată; verificat tonul folosit consecvent în restul aplicației (informal, „tu" — „poți", „alegi", „apeși"), corectat la imperativul informal singular corect: „Tradu". Etichetele proprii ale modulului Antonime & Sinonime nu erau afectate.
- **v11** — Corectată o gaură de siguranță la restaurarea backup-ului: după introducerea prefixelor (v8), un backup vechi (dinainte de v8, cu chei neprefixate) trecea validarea `_app` dar nu restaura de fapt nimic — utilizatorul primea mesajul de succes fără să știe că progresul n-a fost de fapt recuperat. Acum aplicația verifică explicit dacă backup-ul conține măcar o cheie prefixată validă înainte de a cere confirmarea; dacă nu găsește niciuna, oprește procesul cu un mesaj clar („backup dintr-o versiune veche, incompatibil, nu s-a restaurat nimic") în loc de o restaurare falsă. Testat logic pentru 4 scenarii (backup valid, backup vechi neprefixat, aplicație greșită, backup mixt) — toate corecte.
- **v10** — Adăugat modulul **„Antonime & Sinonime"** (nou, construit de la zero pentru greacă — nu exista înainte în această versiune): 59 perechi de antonime + 20 perechi de sinonime (158 de intrări generate, ambele sensuri), exclusiv în greacă, cu distractori din același pool. Testat programatic (simulare completă de rundă mixtă cu alte niveluri) — zero erori. 17 cuvinte esențiale noi adăugate în vocabularul principal ca suport (,,slab", ,,lent", ,,gol", ,,curat" etc.), B1 ajungând la 600 cuvinte rotund. Total vocabular acum: 1858 cuvinte.
- **v9** — Vocabular B1 complet (583 cuvinte), aliniat cu aplicația germană (~591). Total acum: 1841 cuvinte (A1: 650, A2: 608, B1: 583), procesate din rangurile de frecvență ~5000–9000. Chip-ul de nivel B1 din interfață era deja pregătit în UI, doar nepopulat — funcționează acum din prima. Rămâne B2 pentru o fază viitoare.
- **v8** — **Corectare importantă:** toate cele 10 chei de `localStorage` (statistici, „Cuvintele mele", preferințe, streak, istoric AI, cheie API etc.) erau salvate sub nume generice (`wordStats`, `prefs`, `myWords`...), identice cu cele din aplicația germană (Karteikarten). Cum `localStorage` e izolat per **domeniu**, nu per aplicație/pagină, cele două aplicații găzduite pe același domeniu GitHub Pages își amestecau datele — inclusiv istoricul de traduceri AI. Acum toate cheile au prefixul `evanghelismos_`, complet separate. **Notă:** progresul salvat anterior (înainte de v8) rămâne sub cheile vechi, neprefixate, și nu va mai fi citit — practic pornești curat de la această versiune. Aceeași corecție (cu alt prefix, ex. `karteikarten_`) trebuie aplicată și în aplicația germană, ca separarea să fie completă în ambele direcții.
- **v7** — Corectat bara de sus: fix-ul din v4 ascundea complet controalele de zoom pe ecrane înguste (prea agresiv); acum A−/A+ rămân mereu vizibile pe pagina principală, doar procentul și butonul de resetare (mai puțin esențiale) se ascund sub 420px lățime, ca să nu mai împingă Setările pe rândul următor. Butoanele de zoom din Setări au fost verificate programatic (simulare de click real) și funcționează corect din punct de vedere logic — dacă tot par nefuncționale la testare, cel mai probabil cache-ul service worker-ului servește o versiune veche; e nevoie de reinstalare completă (dezinstalare + instalare din nou) sau golire cache browser, nu doar reîncărcare simplă a paginii.
- **v6** — Corectat ștampila de răspuns: varianta pentru răspuns greșit era în română (,,GREȘIT"), inconsecventă cu cea corectă (,,ΣΩΣΤΟ!", în greacă). Acum ambele sunt în greacă: `ΣΩΣΤΟ!` / `ΛΑΘΟΣ!`.
- **v5** — Vocabular A1 și A2 complete (1258 cuvinte total: 650 A1 + 608 A2), aliniat ca volum cu aplicația germană (669 A1 / 591 A2). Procesate rangurile de frecvență ~2500–5000 pentru finalizarea A2. Datele pentru B1 sunt deja extrase, pregătite pentru lotul următor.
- **v4** — Corectat layout-ul barei de sus pe telefoane Android: numele lung al aplicației (Ευαγγελισμός) împingea butonul de Setări (⚙) pe un rând nou, micșorând spațiul aplicației. Numele se trunchiază acum cu „..." dacă nu încape, iar pe ecrane înguste (sub 420px) controalele de zoom din bara de sus se ascund (rămân identic disponibile în Setări) — mic/AI/setări rămân mereu pe același rând.
- **v3** — Vocabular extins: de la 178 la 794 de cuvinte (650 A1 + 144 început de A2), lematizate și traduse manual din rangurile de frecvență 400–2500. Adăugată funcția de detectare a vocii grecești lipsă din sistem, cu ghidare specifică per platformă (Windows/Android — deschidere directă a ecranului de setări; iOS/macOS — instrucțiuni text, din limitări de browser).
- **v2** — Redenumire completă: Ευαγγελισμός (Buna Vestire), dedicată părintelui Daniel. Corectate bug-uri de portare rămase (clasele CSS de gen nu se mapau corect la ο/η/το, referințe reziduale „DE"/„7000 de cuvinte" moștenite din aplicația germană, în secțiunea de Ajutor).
- **v1** — Prima versiune funcțională, portată din arhitectura Karteikarten (germană): motor de flashcards, căutare/adăugare cuvinte, backup, modul AI (Claude) adaptat pentru RO↔EL, iconițe cu steag elen. Vocabular de test: 178 cuvinte A1, lematizate și traduse manual.

## Ce conține

- `index.html` — aplicația
- `vocab-data.js` — baza de vocabular (A1: 650, A2: 608, B1: 600 — complete; B2 urmează)
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
- **Antonime & Sinonime** — nivel dedicat, exclusiv în greacă (59 perechi de antonime + 20 perechi de sinonime, generate automat în ambele sensuri = 158 de întrebări): vezi un cuvânt grecesc, alegi opusul sau apropiatul ca sens, din 4 variante tot grecești, cu ascultare și Glosbe disponibile pe fiecare după ce răspunzi
- **🤖 AI (Claude) — traducere liberă** — adaptată complet pentru perechea română-greacă, inclusiv reconstrucția automată a accentuării grecești (τόνος) pierdute la dictarea vocală (echivalentul grecesc al problemei cratimelor din română)
- Preferințele și statisticile se salvează local, în browser, per dispozitiv

## Ce lipsește față de aplicația germană (intenționat, fază separată)

- Nivelul B2 și „Suplimentar"
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
