# Zasady pracy zespołowej: Git i Claude

Jak pracujemy na wspólnych plikach i z Claude, żeby wszyscy mieli te same, aktualne materiały. Konfiguracja środowiska: [onboarding.md](onboarding.md). Zakres i zadania: [ZAKRES.md](ZAKRES.md).

---

## 1. Zasada główna: GitHub jest źródłem prawdy

Każdy z nas ma dwie kopie materiałów i **obie trzeba odświeżać osobno**:

| Gdzie | Skąd bierze zmiany | Jak odświeżyć |
|---|---|---|
| Folder na dysku | z GitHuba | `git pull` |
| Projekt w Claude | z GitHuba (nie z naszego dysku!) | **Sync now** |

Wniosek: Claude widzi tylko to, co zostało **wypchnięte (`git push`)** na GitHuba. Zmiany zapisane tylko lokalnie są dla niego niewidoczne. Lokalny `git pull` nie odświeża Projektu w Claude i odwrotnie.

---

## 2. Rytm każdej sesji pracy

### Start sesji
- [ ] `git pull` (pobranie zmian kolegów)
- [ ] Jeśli zmieniła się dokumentacja, `INDEKS.md` albo `STATUS.md`: **Sync now** w Projekcie Claude
- [ ] Przeczytać `STATUS.md` (co ustalono, co jest w toku)
- [ ] Zaczynać nową rozmowę z Claude na konkretny temat

### Koniec sesji
- [ ] Zapisać decyzje i przyjęte wartości w `STATUS.md`
- [ ] `git status`, `git add .`, `git commit -m "co zmieniono"`, `git push`
- [ ] Jeśli zmieniły się pliki podpięte do Projektu: **Sync now**
- [ ] Nowe lub usunięte pliki dopisać do `INDEKS.md`

---

## 3. Co gdzie trzymamy

| Rodzaj plików | Przykłady | W Projekcie Claude? |
|---|---|---|
| Stałe materiały referencyjne | dokumentacja prowadzącego, normy, dane wejściowe, `INDEKS.md`, `STATUS.md` | **Tak** (przez integrację GitHub, potem Sync now) |
| Pliki robocze | obliczenia, model, szkice sprawozdania | **Nie**: dołączamy do konkretnej rozmowy, gdy są potrzebne |

Pliki robocze dołączamy po świeżym `git pull`, żeby Claude pracował na aktualnej wersji.

---

## 4. Dobre praktyki: Git

- **Commituj często i małymi porcjami**, z komunikatem mówiącym, co zmieniono („Obliczenia oporów ruchu: wersja 2”, a nie „zmiany”).
- **Zawsze `git pull` przed pracą i przed `git push`.**
- **Jeden plik, jeden właściciel.** Word, PDF i CAD nie scalają się automatycznie. Kto za co odpowiada, jest w [ZAKRES.md](ZAKRES.md).
- Zmiany kolegów nigdy nie nadpisujemy na siłę (nie używamy `git push --force`).
- Jeśli `push` jest odrzucony: najpierw `git pull`, rozwiąż ewentualny konflikt, potem `push`. W razie wątpliwości zapytaj zespół, zanim cokolwiek skasujesz.
- Do repozytorium nie trafiają: pliki >100 MB, dane osobowe, hasła i klucze, pliki tymczasowe (ujęte w `.gitignore`).
- Preferuj formaty tekstowe (Markdown, CSV, kod) tam, gdzie się da. Dla Gita są najwygodniejsze, a dla Claude najpewniej odczytywane.

---

## 5. Dobre praktyki: praca z Claude

- **Jedna rozmowa = jeden temat** (np. „obliczenia hamulców”, „cykl jazdy”).
- Podawaj dane wejściowe w pytaniu: masa, założenia, źródło wartości.
- **Claude nie zapisuje nic do repozytorium.** Wyniki kopiujesz sam do plików, a potem commitujesz.
- Historia rozmów nie jest wspólna. Wszystko, co ma przetrwać (decyzje, przyjęte wartości, uzasadnienia), trafia do `STATUS.md`.
- **Weryfikuj obliczenia, normy i dane liczbowe w źródle.** Claude może się pomylić.
- Przed oddaniem poproś o recenzję według kryteriów zaliczenia i o symulację obrony.
- Nie wklejaj do rozmów danych osobowych.
- Sprawdź regulamin uczelni i zdanie prowadzącego w sprawie użycia AI i w razie potrzeby wspomnij o tym w sprawozdaniu.

---

## 6. Obsidian

- Otwieramy **folder repozytorium jako vault** (*Open folder as vault*). Katalog `.obsidian/` jest w `.gitignore`, więc ustawienia są lokalne i każdy ma własne.
- **Linki:** używamy standardowych linków Markdown `[tekst](plik.md)`, a nie `[[wikilinków]]`, bo te drugie nie działają na GitHubie. W Obsidianie: *Settings → Files and links* → wyłącz „Use [[Wikilinks]]” i ustaw „New link format” na „Relative path to file”.
- **Załączniki:** ustaw „Default location for new attachments” na wybrany folder (np. `zalaczniki/`), żeby obrazy nie lądowały w głównym katalogu repozytorium.
- Obsidian zapisuje zmiany na dysk od razu, ale **sam nie robi `git pull` ani `git push`**. Robimy to ręcznie (terminal lub GitHub Desktop). Wtyczka społecznościowa „Obsidian Git” to opcja na później. Na początek lepiej bez automatycznych commitów, bo utrudniają panowanie nad konfliktami.
- Pliki współdzielone (`ZAKRES.md`, `STATUS.md`, `INDEKS.md`) edytuj krótko i od razu rób `commit` i `push`. Zaznaczenie checkboxa w Obsidianie to taka sama edycja pliku jak każda inna i może wywołać konflikt.
- Piszemy **standardowym Markdownem**, bez składni specyficznej dla Obsidiana (wikilinki, callouts, Dataview). Inaczej tekst jest nieczytelny na GitHubie, a Claude widzi surowy tekst bez renderowania.
- Pliki DOCX, XLSX i CAD edytujemy w ich własnych programach. Obsidian służy do plików `.md`, a PDF-y i obrazy może tylko podglądać.

---

## 7. Typowe problemy

| Problem | Co sprawdzić |
|---|---|
| Claude nie widzi nowego pliku | Czy plik jest wypchnięty (`git push`)? Czy kliknięto **Sync now**? Czy folder jest zaznaczony w „Configure files”? |
| Claude widzi starą wersję | **Sync now** i nowa rozmowa |
| Nie widać PDF/DOCX z repozytorium | Wgraj plik ręcznie do wiedzy Projektu (limit 30 MB na plik) |
| `git push` odrzucony | `git pull`, rozwiąż konflikt, ponów `push` |
| Plik >100 MB | Usuń z commita, trzymaj poza repozytorium lub podziel |

---

## 8. Historia zmian

| Data       | Zmiana           | Kto              |
| ---------- | ---------------- | ---------------- |
| 2026-11-07 | Utworzenie pliku | Miłosz Bagrowski |
