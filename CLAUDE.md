# Strona Pauliny Korzeniewskiej: notatki dla Claude

Ten plik opisuje projekt dla asystenta Claude. Przeczytaj go w całości, zanim zaczniesz zmieniać stronę.

## Czym jest projekt

To jednostronicowa strona-wizytówka Pauliny Korzeniewskiej. Paulina jest poetką, autorką książki dla dzieci, scenarzystką i tłumaczką języka angielskiego. Ma doktorat z nauk humanistycznych. Strona jest po polsku.

Paulina edytuje stronę sama, z pomocą Claude. Gotowe pliki trafiają na serwer jej znajomego (Łukasz), który wgrywa je przez FTP.

## Pliki

```
index.html   cała strona: HTML + CSS + mały skrypt menu, w jednym pliku
img/         zdjęcia, okładki (JPG) i og.jpg (obraz do udostępniania linku, 1200×630)
fonts/       kroje pisma (woff2, licencja SIL OFL)
favicon.ico, apple-touch-icon.png   ikony strony
robots.txt   na czas wersji roboczej blokuje roboty (patrz niżej)
CLAUDE.md    ten plik
INSTRUKCJA-DLA-PAULINY.txt   instrukcja dla Pauliny (nie jest częścią strony)
```

Na serwer trafiają tylko `index.html`, `robots.txt`, `favicon.ico`, `apple-touch-icon.png`, `img/` i `fonts/`.

**Wersja robocza (noindex):** `index.html` ma `<meta name="robots" content="noindex, nofollow">`, a `robots.txt` ma `Disallow: /`. Przed publikacją na docelowej domenie trzeba to zdjąć (instrukcja w komentarzach obu plików) oraz odkomentować w `<head>` znaczniki `og:url`, `og:image`, `canonical` i wpisać prawdziwą domenę zamiast `DOMENA`.

## Zasady, których trzymaj się zawsze

1. **Zmieniaj tylko to, o co prosi Paulina.** Nie przepisuj innych sekcji „przy okazji” i nie zmieniaj treści bez prośby.
2. **Edytuj plik `index.html` w miejscu.** Wszystko jest w jednym pliku. Nie rozdzielaj go na osobne pliki CSS/JS bez wyraźnej prośby.
3. **Bez zewnętrznych zasobów.** Strona nie ładuje niczego z internetu: żadnych Google Fonts, CDN ani skryptów zewnętrznych. Fonty są w `fonts/` i są wpięte przez `@font-face` na początku stylów. To świadoma decyzja ze względu na RODO.
4. **Nowe zdjęcia** wgrywaj do `img/` (JPG, do ok. 300 KB, krótka nazwa bez polskich znaków i spacji). W `<img>` zawsze podawaj `alt`, `width`, `height` i `loading="lazy"`. W CSS obrazki potrzebują `height: auto`, bo atrybut `height` nadpisałby proporcje.
5. **Polska typografia:** cudzysłowy „…” (wyjątek: motto po angielsku w “…”), półpauza „–” z odstępami (nie łącznik „-”), twarda spacja `&nbsp;` po jednoliterowych spójnikach i przyimkach (w, z, i, o, a, u) oraz w „1,6&nbsp;MB”.
6. **Ikony LinkedIn, Facebook i Instagram** pochodzą z Font Awesome Free (licencja CC BY 4.0). Komentarz z licencją wewnątrz każdego `<svg>` musi zostać.
7. **Sprawdzaj wersję na telefon.** Układ zmienia się przy szerokości 1023 px (tablet) i 700 px (telefon). Po zmianie upewnij się, że nic nie wychodzi poza ekran przy 390 px szerokości.
8. **Kontrast:** tekst ma co najmniej 4.5:1 względem tła. Używaj kolorów z tokenów niżej, nie wymyślaj nowych.

## Styl (wersja 3, „redakcyjna”)

Inspiracja: redakcyjna strona o poecie A.R. Ammonsie. Charakter: szary papier z delikatną fakturą, czerń, ogromne wersaliki, czarno-białe zdjęcia, cienkie linie zamiast cieni.

**Kolory (zmienne CSS w `:root`):**

| zmienna | wartość | rola |
| --- | --- | --- |
| `--paper` | #efeeea | tło strony (z fakturą `--noise`) |
| `--paper-2` | #e4e3de | obecnie nieużywane (od 9 XI 2026 okładki stoją bez tła) |
| `--ink` | #121212 | tekst, linie |
| `--muted` | #5a5955 | tekst pomocniczy |
| `--night` | #0e0e0e | ciemne tło: sekcja Tłumaczenia, stopka |
| `--on-night` | #ecebe7 | tekst na ciemnym tle |
| `--on-night-muted` | #a8a7a2 | tekst pomocniczy na ciemnym tle |

**Kroje:**

- `--grot`: **Inter Tight** (400, 500). Duże wersaliki (imię, nazwy sekcji, tytuły scenariuszy, „Kilka lat z Netflixem”), tekst ciągły, etykiety.
- `--serif`: **Newsreader** (400 i kursywa). Kursywy, lead, podpisy pod okładkami, lata przy scenariuszach.
- Cały górny pasek (imię i nazwisko, linki menu, przycisk „Menu”): Inter Tight 500, czyli najgrubsza odmiana w `fonts/`. Nie dodawaj `font-weight: 700`, bo przeglądarka sztucznie pogrubi krój.
- Duże wersaliki: `font-weight: 500; text-transform: uppercase; letter-spacing: -0.045em; line-height: .84`.

**Elementy:**

- Górny pasek `.bar`: imię i nazwisko po lewej (link `#top`, przewija na sam początek strony), menu po prawej. Na tablecie i telefonie przycisk „Menu” otwiera pełnoekranowe `.overlay`. **Nie nadawaj żadnemu elementowi `id="top"`**: wtedy przeglądarka przewija do samej góry strony; gdyby miał je przyklejony pasek, kliknięcie nic by nie dawało.
- Hero (`.hero`, od 9 XI 2026) to jeden blok w dwóch kolumnach (od 1024 px, siatka 12 kolumn, proporcje 7:5):
  - lewa kolumna (1–7): na górze „PAULINA / KORZENIEWSKA” wersalikami (`.name`) i pod nim „Scenarzystka, poetka, tłumaczka” (`.hero-pl`), na dole motto (`.quote`) wyrównane do dolnej krawędzi zdjęcia;
  - prawa kolumna (8–12): czarno-białe zdjęcie 4:5 (`.hero-photo`).
  - Rozmiar imienia liczy się od szerokości kolumny (jednostki `cqi`, kontener `.hero-id`), więc „KORZENIEWSKA” zawsze się w niej mieści. Zdjęcie ma `max-height`, żeby cały blok mieścił się na pierwszym ekranie laptopa.
  - Na tablecie i telefonie jedna kolumna, w kolejności z kodu: imię, podpis, zdjęcie, motto.
  - Nie wracaj do dawnego układu (imię na całą szerokość, motto w osobnej sekcji) bez prośby.
- Motto `.quote`: angielski cytat wersalikami, ok. 40% wielkości imienia, w trzech linijkach (`.l1` z wysuniętym cudzysłowem, żeby litery równały się z imieniem; `.l2` z wcięciem; `.l3` „keeps me awake.”, bez linii). Tuż pod nim podpis „— Anne Sexton”, żeby nikt nie wziął cytatu za słowa Pauliny. Bez dużego szarego cudzysłowu w tle.
- Każda sekcja ma nagłówek `.sec-head` z nazwą sekcji wersalikami (`h2`), bez podtytułów obok.
  - Linia oddzielająca nad tytułem jest tylko w „O mnie” i „Twórczość”. „Tłumaczenia” i „Napisz do mnie” mają klasę `no-line`: oddziela je krawędź ciemnego tła.
  - **Odstępy (od 9 XI 2026):** jeden odstęp S = `var(--section)` (64 px, na telefonie 40 px).
    - Sekcja z linią: koniec poprzedniej treści → linia = S, linia → górna krawędź wielkich liter tytułu = S.
    - Sekcja bez linii: krawędź ciemnego tła → wielkie litery tytułu = S.
    - Ciemna sekcja: treść przed nią → krawędź tła = S, koniec jej treści → dolna krawędź tła = S.
    - Kreski nad Ó, Ś, Ć mieszczą się w odstępie nad tytułem i nie dotykają linii.
    - Nie dodawaj sekcjom `padding-bottom` ani marginesów na końcu treści, bo rozjadą się odstępy.
  - **Wielkość tytułu:** 80% wielkości imienia z hero (nigdy większa niż imię), liczona tak samo jak imię (kontener `.sec-head`, jednostki `cqi`).
- Podsekcje oznacza `.label` (nagłówek `h3`): **białe wersaliki na czarnym tle** (Inter Tight 500, 15 px, rozstrzelone, `letter-spacing: .16em`), bez linii, np. „Dla dzieci”, „Poezja”, „Scenariusze”. Tytuł książki w bloku „Dla dzieci” to `h4`.
- Siatka 12 kolumn (`.grid12`). Treść zwykle zaczyna się od 5.–7. kolumny, zdjęcia stoją w kolumnach 1–3/4.
- **Okładki książek mają jedną szerokość** (od 9 XI 2026): na komputerze 3 kolumny siatki, na tablecie 1/3 szerokości, na telefonie do 300 px. Bez szarego tła pod okładką. Wysokość wynika z proporcji okładki (nie przycinaj okładek), więc wyższe okładki wystają w górę, a podpisy i przyciski w rzędzie stoją na jednej linii (`.books` + `subgrid`).
  - Okładka „Usta Vivien Leigh” (oryginalnie 480×969, wąska) jest poszerzona do proporcji pozostałych (656×969) przez dołożenie jej białego tła po bokach, bez skalowania i przycinania grafiki. Skan był przycięty z lewej, więc ilustracja kończy się tam prostą krawędzią. Jeśli Paulina ma lepszy skan, podmień plik.
  - Nowe okładki najlepiej w proporcjach ok. 2:3 (szerokość ≈ 0,68 wysokości), żeby rząd był równy.
- **Przycisk „Kup teraz”** (`.buy`) jest wyśrodkowany pod każdą książką: w Poezji pod opisem tomiku, w bloku „Dla dzieci” pod okładką. Na razie to `<a class="buy">` bez `href`, więc nie reaguje na kliknięcie. Jak podpiąć sklep: patrz niżej.
- Zdjęcia osób są czarno-białe (klasa `.bw`). Okładki książek zostają kolorowe.
- Bez zaokrągleń, bez cieni na elementach interfejsu. Wyjątkiem jest delikatny cień samych okładek.
- **Linie (od 9 XI 2026):** zostały tylko linie nad tytułami „O mnie” i „Twórczość” oraz krótka kreska nad „Scenarzystka, poetka, tłumaczka” w hero. Tytuły „Tłumaczenia” i „Napisz do mnie”, podtytuły, metryczka książki, kolumny w Kontakcie i scenariusze są bez linii. Nie dodawaj nowych linii bez prośby, bo strona staje się nieczytelna.

## Sekcje (kolejność na stronie)

1. **Hero**: imię i nazwisko, „Scenarzystka, poetka, tłumaczka”, portret i motto „The business of words keeps me awake” – cytat Anne Sexton (nie Pauliny). Wszystko w jednym bloku (opis w „Elementy” wyżej).
2. ~~Motto jako osobna sekcja~~ – od 9 XI 2026 motto jest częścią hero.
3. **O mnie** (`#o-mnie`): bez podtytułu, zdjęcie (`img/portret-2.jpg`) i jeden lead. Bez liczb i statystyk.
4. **Twórczość** (`#tworczosc`):
   - **Dla dzieci**: wyróżniony blok „U Twojego Boku” (okładka, opis, metryczka `.meta` tylko: ilustracje i rok wydania; „Kup teraz” pod okładką).
   - **Poezja**: siatka `.books` z okładkami. Tomiki od najnowszego: „Mniej” (2022), „Pogodna biel dobrego samopoczucia” (2016, Dom Literatury w Łodzi), „Usta Vivien Leigh” (2011). Bez liczby stron. Pod każdym opisem „Kup teraz”.
   - **Scenariusze**: programy rozwojowe i wyróżnienia (`.script-list`): siatka bez linii (3 kolumny, tablet 2, telefon 1), w każdej pozycji rok, nazwa i opis. Script Fiesta 2025, Final Draft Special Award 2025, Young Horizons Lab 2025, Scenarzystki na Horyzoncie 2026, Warsaw Next 2026, ScriptzONA 2026.
5. **Tłumaczenia** (`#tlumaczenia`, ciemne tło): bez linii nad tytułem i bez podtytułu (dawny „Przekład” usunięty 9 XI 2026), jeden akapit o przekładzie audiowizualnym i zaproszenie do kontaktu.
6. ~~Dydaktyka~~ – sekcja usunięta ze strony i z menu (na prośbę Pauliny).
7. **Kontakt** (`#kontakt`): tytuł sekcji „Napisz do mnie” (w menu nadal „Kontakt”), bez linii nad tytułem i bez podtytułu, duży e-mail bez podkreślenia (paulinakorzeniewska@gmail.com), kolumny „Współpraca” i „W sieci” (LinkedIn, Facebook, Instagram z ikonkami).
8. **Stopka**: „Copyright © 2026 Paulina Korzeniewska • Wszystkie prawa zastrzeżone | All rights reserved”.

Głos: sekcje są w pierwszej osobie („Jestem…”, „Od ponad dekady zajmuję się…”).

## Do uzupełnienia

- Linki czterech przycisków „Kup teraz” (gdy Paulina poda adresy sklepów).

## Jak dodać kolejny tomik

Skopiuj jedną `<figure class="book">` z sekcji Poezja (razem z `<span class="cap">` i przyciskiem `<a class="buy">`). Podmień plik okładki w `img/`, tekst `alt`, `width` i `height` (prawdziwe wymiary pliku), tytuł w `<b>` i linijki metryczki. Tomiki układaj od najnowszego. Szerokość okładki ustawia się sama, nie dodawaj jej w CSS.

## Jak podpiąć przycisk „Kup teraz”

Dopisz do `<a class="buy">` adres sklepu, np.:

```html
<a class="buy" href="https://sklep.example/ksiazka" target="_blank" rel="noopener">Kup teraz<span class="sr-only"> (otwiera się w nowej karcie)</span></a>
```

Bez `href` przycisk nie reaguje na kliknięcie. Przed publikacją strony albo podepnij wszystkie linki, albo usuń przyciski bez linku, bo nieaktywny przycisk myli odwiedzających.

## Podgląd

Plik `index.html` otwiera się wprost w przeglądarce, podwójnym kliknięciem. Po każdej zmianie wystarczy odświeżyć kartę. Wersję na telefon sprawdzisz, zwężając okno albo w trybie urządzenia mobilnego w narzędziach deweloperskich przeglądarki.
