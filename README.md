# Paulina Korzeniewska – strona internetowa

Jednostronicowa strona-wizytówka Pauliny Korzeniewskiej: scenarzystki, poetki i tłumaczki.
Cała strona to jeden plik `index.html` (HTML, style i mały skrypt menu). Nie ma zależności ani budowania.
Strona nie ładuje niczego z zewnętrznych serwerów, bo fonty są w `fonts/` (ze względu na RODO).

## Pliki

| plik / folder | co to jest |
| --- | --- |
| `index.html` | cała strona: treść, style i skrypt |
| `img/` | portrety, okładki i `og.jpg` (obraz do udostępniania linku, 1200×630) |
| `fonts/` | kroje Inter Tight i Newsreader (woff2) |
| `favicon.ico`, `apple-touch-icon.png` | ikony strony |
| `robots.txt` | na czas wersji roboczej blokuje roboty wyszukiwarek |
| `CLAUDE.md` | opis projektu i zasady edycji (dla Claude i dla ludzi) |
| `INSTRUKCJA-DLA-PAULINY.txt` | jak edytować stronę z pomocą Claude |

Na serwer trafiają tylko: `index.html`, `img/`, `fonts/`, `favicon.ico`, `apple-touch-icon.png` i `robots.txt`.

## Podgląd

Otwórz `index.html` w przeglądarce (dwuklik). Wersję na telefon sprawdzisz, zwężając okno
albo w trybie urządzenia mobilnego w narzędziach deweloperskich przeglądarki.

## Status: wersja robocza

Przed publikacją na docelowej domenie:

1. Usuń `<meta name="robots" content="noindex, nofollow">` z `index.html`.
2. W `robots.txt` zamień `Disallow: /` na `Allow: /`.
3. W `<head>` odkomentuj `og:url`, `og:image` i `canonical` i wpisz prawdziwą domenę zamiast `DOMENA`.
4. Podepnij linki czterech przycisków „Kup teraz” albo usuń przyciski bez linku (opis w `CLAUDE.md`).

## Prawa i licencje

- Teksty, zdjęcia i okładki należą do ich autorów: Pauliny Korzeniewskiej, fotografów, ilustratorów i wydawców.
  Wszystkie prawa zastrzeżone.
- Fonty Inter Tight i Newsreader: SIL Open Font License 1.1 (https://openfontlicense.org).
- Ikony LinkedIn, Facebook i Instagram: Font Awesome Free, licencja CC BY 4.0 (informacja w kodzie każdej ikony).
