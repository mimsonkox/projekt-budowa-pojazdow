# Onboarding: jak przygotować środowisko do pracy

Projekt zaliczeniowy z przedmiotu **Budowa pojazdów drogowych** (zespół 4-osobowy). Ten plik opisuje, jak w kilkanaście minut przygotować komputer i konto Claude, żeby pracować na tych samych materiałach co reszta zespołu.

Spis plików i linków zewnętrznych: [INDEKS.md](INDEKS.md). Aktualny stan prac: `STATUS.md`.

---

## 1. Konto GitHub i dostęp do repozytorium

1. Załóż konto na <https://github.com> (jeśli jeszcze go nie masz).
2. Podaj swój login GitHub osobie, która założyła repozytorium. Dodaje Cię jako współpracownika (*Settings → Collaborators*).
3. Zaakceptuj zaproszenie (przychodzi e-mailem i pojawia się w powiadomieniach GitHuba).

Repozytorium jest **prywatne**: bez zaproszenia go nie zobaczysz.

## 2. Instalacja klienta Git (Windows)

1. Pobierz instalator ze strony <https://git-scm.com/download/win> i uruchom go. Ustawienia domyślne są w porządku (instalator dodaje też Git Credential Manager, który obsługuje logowanie do GitHuba).
2. Otwórz **Git Bash** albo **PowerShell** i sprawdź instalację:
   ```
   git --version
   ```
3. Skonfiguruj dane autora (jednorazowo, użyj e-maila z konta GitHub):
   ```
   git config --global user.name "Imię Nazwisko"
   git config --global user.email "twoj@email.pl"
   ```

> Wolisz interfejs graficzny? Możesz zamiast terminala użyć **GitHub Desktop** (<https://desktop.github.com>). Wszystkie poniższe operacje mają tam swoje przyciski.

## 3. Pobranie repozytorium

```
cd "$HOME\Documents"
git clone ADRES_REPOZYTORIUM
```

`ADRES_REPOZYTORIUM` to adres w formacie `https://github.com/LOGIN/NAZWA.git` (przycisk **Code** na stronie repozytorium). Przy pierwszym razie otworzy się okno logowania do GitHuba w przeglądarce.

### Codzienna praca z repozytorium

Przed rozpoczęciem pracy:
```
git pull
```
Po zakończeniu pracy:
```
git add .
git status
git commit -m "Krótki opis zmian"
git push
```

Zasady, które oszczędzają nerwów:
- **Zawsze `git pull` przed rozpoczęciem pracy.**
- Nie edytujcie jednocześnie tego samego pliku. Pliki Word, PDF i CAD nie scalają się automatycznie. Ustalcie, kto za który plik odpowiada.
- Komunikat commita ma mówić, co zmieniono (np. „Obliczenia hamulców: wersja 2”).
- Nie wrzucajcie do repozytorium plików większych niż 100 MB (GitHub je odrzuca) ani danych osobowych.

## 4. Konto Claude i utworzenie Projektu

1. Załóż konto na <https://claude.ai> (lub zaloguj się). Dostępność Projektów i limity zależą od planu. Sprawdź w aplikacji, co masz do dyspozycji.
2. Wejdź w **Projects → New project** i nadaj nazwę (np. „Budowa pojazdów drogowych”).
3. W polu **instrukcji projektu** wklej:

   > Jesteś prowadzącym i ekspertem od budowy pojazdów drogowych na Politechnice Poznańskiej. Pracuję z Tobą nad projektem zaliczeniowym w 4-osobowym zespole (3. rok, mechanika i budowa pojazdów). Dokumentacja, wytyczne i warunki zaliczenia są w plikach Projektu: traktuj je jako nadrzędne źródło wymagań.
   >
   > Zasady pracy:
   > - Odpowiadaj po polsku, językiem technicznym, ale tłumacz trudniejsze pojęcia.
   > - Zachowuj się jak wymagający, ale pomocny prowadzący: zadawaj pytania naprowadzające, wskazuj błędy w założeniach i obliczeniach, wymagaj uzasadnienia decyzji projektowych.
   > - Przy obliczeniach pokazuj wzory, jednostki i założenia. Zaznacz, jeśli czegoś nie jesteś pewien lub wartość trzeba zweryfikować w normie lub katalogu.
   > - Nie wymyślaj danych, norm ani numerów przepisów. Jeśli czegoś nie ma w plikach, powiedz to wprost.
   > - Na koniec dłuższych odpowiedzi dawaj krótkie „następne kroki".
   > - Pomagaj mi zrozumieć, nie tylko dostarczaj gotowe rozwiązania: celem jest, żebym umiał obronić projekt.

## 5. Podpięcie repozytorium do Projektu

1. W Projekcie, w sekcji wiedzy projektu, kliknij **„+” → GitHub**.
2. Zaloguj się i **nadaj Claude dostęp do prywatnego repozytorium** (wystarczy dostęp tylko do tego jednego repozytorium).
3. Wybierz repozytorium i zaznacz **tylko stałe materiały referencyjne**: foldery z dokumentacją, `INDEKS.md`, `STATUS.md`. Nie zaznaczaj całego repozytorium, bo wszystko zajmuje miejsce w kontekście.
4. Po każdej zmianie w repozytorium kliknij **Sync now**. Synchronizacja nie jest automatyczna.

Pliki zmieniane na bieżąco (obliczenia, szkice sprawozdania) dołączajcie do konkretnej rozmowy, kiedy ich potrzebujecie.

### Test poprawności

W nowej rozmowie w Projekcie napisz: *„Wymień wszystkie pliki z dokumentacji, które widzisz”*. Porównaj odpowiedź z `INDEKS.md`.
- Jeśli brakuje plików PDF lub DOCX, wgraj je ręcznie do bazy wiedzy Projektu (limit: 30 MB na plik; obsługiwane m.in. PDF, DOCX, XLSX, CSV, TXT, JSON).
- Rysunki techniczne i schematy wgrywajcie jako PDF, bo wtedy Claude może je zobaczyć. W innych formatach przetwarzany jest zwykle sam tekst.

## 6. Dobre nawyki w pracy z Claude

- **Jedna rozmowa = jeden temat** (np. „dobór układu napędowego”, „obliczenia hamulców”).
- Podawaj dane wejściowe w pytaniu (masa, rozstaw osi, założenia).
- **Weryfikujcie obliczenia i przepisy w źródle.** Claude może się pomylić.
- Wnioski i przyjęte wartości wpisujcie do `STATUS.md`. Historia rozmów nie jest wspólna dla zespołu.
- Przed oddaniem poproście o recenzję według kryteriów zaliczenia oraz o symulację obrony.
- Sprawdźcie, czy regulamin uczelni i prowadzący zezwalają na korzystanie z AI, i w razie potrzeby zaznaczcie to w sprawozdaniu.
