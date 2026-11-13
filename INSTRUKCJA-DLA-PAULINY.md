# Edycja strony przez Claude

Instrukcja dla Pauliny: jak połączyć Claude z GitHubem i zmieniać stronę **paulinakorzeniewska.com**
zwykłymi poleceniami, pisanymi po polsku.

## Co będzie potrzebne

- **Płatne konto Claude**, plan Pro lub wyższy. W darmowym planie ta funkcja (Claude Code w przeglądarce) nie działa.
- **Login i hasło do GitHuba** (konto PaulinaKorzeniewska). Hasło wpisujesz tylko na stronie github.com.
- **Komputer z przeglądarką** (Chrome, Edge, Firefox albo Brave). Nic nie trzeba instalować.

## Krok 1. Połącz Claude z GitHubem

Robisz to tylko raz. Zajmuje około 5 minut.

1. Otwórz stronę [claude.ai/code](https://claude.ai/code) i zaloguj się do Claude tak jak zwykle.
2. Claude poprosi o połączenie z GitHubem. Kliknij przycisk połączenia
   (nazywa się np. **Connect GitHub** albo **Sign in with GitHub**).
3. Otworzy się strona GitHuba. Jeśli trzeba, zaloguj się swoim loginem i hasłem do GitHuba,
   a potem kliknij zielony przycisk zgody (**Authorize**). Wrócisz automatycznie do Claude.
4. Jeśli Claude zaproponuje instalację **Claude GitHub App**, zgódź się, ale tylko dla strony:
   - wybierz **Only select repositories** (tylko wybrane),
   - zaznacz **strona**,
   - kliknij **Install**.

   Jeśli wolisz, możesz kliknąć **Skip**. Strona jest publiczna, więc zadziała i bez tego.
5. Claude sam utworzy ustawienia o nazwie **Default**. Niczego w nich nie zmieniaj.

## Krok 2. Poproś o zmianę

1. Wejdź na [claude.ai/code](https://claude.ai/code).
2. Pod polem do pisania kliknij wybór repozytorium i wybierz **PaulinaKorzeniewska/strona**.
   Gałąź **main** zostaw bez zmian.
3. Obok wybierz tryb **Accept edits** (Claude od razu wprowadzi zmiany).
   Jeśli przy większej zmianie wolisz najpierw zobaczyć plan, wybierz **Plan**.
4. Napisz po polsku, co chcesz zmienić, i naciśnij Enter. Podaj nazwę sekcji:
   *O mnie*, *Twórczość*, *Tłumaczenia*, *Napisz do mnie*.
5. Claude sam przeczyta opis Twojej strony (plik `CLAUDE.md`), więc nie musisz go wklejać.
   Praca trwa zwykle kilka minut. Jeśli Claude o coś zapyta, odpowiedz w czacie.
6. Gdy skończy, z prawej strony pojawi się karta **Changes** z liczbami, np. **+3 −1**.
   Kliknij je, żeby zobaczyć zmiany: na zielono to, co dodane, na czerwono to, co usunięte.
   Jeśli coś jest nie tak, napisz w czacie, co poprawić.

## Krok 3. Opublikuj zmianę

> **Strona jest już publiczna.** Po zatwierdzeniu zmiany (punkt 3) zobaczą ją wszyscy
> odwiedzający paulinakorzeniewska.com.

1. Na karcie **Changes** kliknij **Create PR**. To tworzy „propozycję zmiany”.
2. Kliknij link do tej propozycji. Otworzy się strona GitHuba.
3. Kliknij zielony przycisk **Merge pull request**, a potem **Confirm merge**.
   Dopiero teraz zmiana trafia na stronę.
4. Po 1–2 minutach otwórz [paulinakorzeniewska.com](https://paulinakorzeniewska.com) i odśwież stronę
   (Ctrl+F5, na Macu Cmd+Shift+R). Sprawdź też na telefonie.

## Przykładowe polecenia

- W sekcji Twórczość, w Scenariuszach, dodaj na końcu: „Nazwa programu”, opis „Finalistka”, rok 2027.
- W sekcji O mnie zmień zdanie zaczynające się od „Napisałam trzy tomy” na: …
- Podepnij przycisk „Kup teraz” przy tomiku „Mniej” do adresu: https://…
- Sprawdź, czy strona dobrze wygląda na telefonie, i napisz mi, co warto poprawić. Na razie niczego nie zmieniaj.

Jedna sprawa w jednej rozmowie. Następną zmianę zacznij jako nową rozmowę na claude.ai/code,
gdy poprzednia jest już opublikowana.

## Nowe zdjęcie lub okładka

Zdjęcie trzeba najpierw wgrać na GitHuba. Claude nie zapisze zdjęcia wklejonego do czatu jako pliku strony.

1. Przygotuj plik JPG do około 300 KB. Nazwa bez polskich liter i spacji, np. `okladka-nowy-tomik.jpg`.
2. Na [github.com/PaulinaKorzeniewska/strona](https://github.com/PaulinaKorzeniewska/strona) otwórz folder **img**.
3. Kliknij **Add file** → **Upload files**, przeciągnij zdjęcie i na dole kliknij **Commit changes**.
4. Na claude.ai/code napisz np.: „Dodaj w Poezji nowy tomik: tytuł …, wydawnictwo …, rok …,
   okładka img/okladka-nowy-tomik.jpg”. Potem opublikuj jak w kroku 3.

## Coś poszło nie tak?

- Na GitHubie wejdź w zakładkę **Pull requests** → **Closed**, otwórz ostatnią zmianę i kliknij **Revert**.
  Powstanie nowa propozycja, którą zatwierdzasz jak w kroku 3 (**Merge pull request** → **Confirm merge**).
- Albo napisz na claude.ai/code: „Cofnij ostatnią zmianę na stronie” i opublikuj jak zwykle.
- Zamknięcie karty przeglądarki nie przerywa pracy Claude. Do rozmowy wrócisz z listy po lewej na claude.ai/code.

## Dobre zwyczaje

- Przed zmianami daj znać Łukaszowi, żebyście nie poprawiali strony w tym samym czasie.
- Nigdy nie podawaj Claude haseł. Hasło do GitHuba wpisujesz tylko na github.com.
- Praca Claude wlicza się do limitów Twojego planu.

## Słowniczek

- **Repozytorium** – folder z plikami Twojej strony na GitHubie: PaulinaKorzeniewska/strona.
- **Gałąź main** – główna wersja strony. To ona jest widoczna pod paulinakorzeniewska.com.
- **PR (pull request)** – propozycja zmiany. Niczego nie zmienia na stronie, dopóki jej nie zatwierdzisz.
- **Merge** – zatwierdzenie propozycji. Po nim zmiana jest na stronie.
