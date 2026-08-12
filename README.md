# Ευαγγελισμός — Flashcards Ελληνικά ⇄ Română (Buna Vestire)

Aplicație dedicată părintelui Daniel.

Aplicație de exersat vocabular grec-român, sub formă de PWA (Progressive Web App) instalabilă pe telefon.

**⚠️ Versiune de test (v0.1)** — vocabularul conține momentan doar ~178 de cuvinte de nivel A1 (cele mai frecvente cuvinte din greaca modernă), ca punct de plecare pentru validarea arhitecturii înainte de construirea vocabularului complet A1–B2. Modulele „Antonime & Sinonime" și „Conjugare verbe" (prezente în aplicația soră de germană) nu sunt încă implementate — sunt planificate pentru o fază separată, cu date construite specific pentru greacă.

## Ce conține

- `index.html` — aplicația
- `vocab-data.js` — baza de vocabular (A1, ~178 cuvinte, versiune de test)
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

- Nivelurile B1/B2/Suplimentar (doar A1 populat momentan)
- Modulul „Antonime & Sinonime"
- Modulul „Conjugare verbe"
- Vocabular de specialitate (echivalentul „Îngrijire" din aplicația germană)

## Instalare pe telefon

1. Deschide link-ul GitHub Pages al acestui repository, în Chrome (Android) sau Safari (iOS)
2. Din meniul browserului, alege "Adaugă la ecranul principal" / "Instalează aplicația"
3. Aplicația apare cu propria iconiță și funcționează parțial offline

## Surse și atribuiri

- **Selecția cuvintelor A1** e construită din rangul de frecvență reală de utilizare a limbii grecești moderne, pe baza listei [hermitdave/FrequencyWords](https://github.com/hermitdave/FrequencyWords) (`content/2016/el/el_50k.txt`, derivată din corpus OpenSubtitles), licență **MIT**.
- Spre deosebire de aplicația franceză (lematizată programatic cu spaCy `fr_core_news_sm`), acest prim lot de 178 de cuvinte a fost **lematizat și verificat integral manual** — formele flexionate din topul de frecvență brut (ex. toate formele lui „a avea": έχω/έχεις/έχει/είχα...) au fost reduse manual la lema corectă. Loturile viitoare, mai mari, vor evalua dacă merită folosit spaCy `el_core_news_sm` (cunoscut cu probleme de nedeterminism la lematizare, per issue-uri publice) sau dacă verificarea manuală rămâne mai eficientă la acest volum.
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
