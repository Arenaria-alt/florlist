# FlorList — Arenaria

Aplikacja webowa do terenowej inwentaryzacji florystycznej. Działa jako PWA (Progressive Web App) — można ją zainstalować na ekranie głównym telefonu i używać jak natywną aplikację.

---

## Instalacja na telefonie

**Android (Chrome):**
1. Otwórz stronę aplikacji w Chrome
2. Kliknij ⋮ → *Dodaj do ekranu głównego*

**iPhone (Safari):**
1. Otwórz stronę aplikacji w Safari
2. Kliknij ikonę udostępniania □↑ → *Dodaj do ekranu głównego*

---

## Funkcje

### 🔍 Szukaj
Główny panel do wyszukiwania gatunków i dodawania ich do listy.

- **Wyszukiwanie tekstowe** — wpisz min. 2 znaki: akronim, nazwę łacińską lub polską. Wyniki pojawiają się na bieżąco.
- **Filtr grup** — przyciski *Wszystkie / Naczyniowe / Mszaki / Porosty* zawężają pulę wyszukiwania.
- **Rozpoznawanie głosowe 🎤** — przycisk mikrofonu umożliwia dyktowanie nazwy gatunku (działa w Chrome na Androidzie). Wystarczy powiedzieć np. *„Pinus sylvestris"* lub *„sosna zwyczajna"*.
- **Dodawanie do listy** — kliknięcie wiersza wyników lub przycisku `+` dodaje gatunek do aktywnej listy. Gatunki już dodane są oznaczone i wyszarzone.

### 📋 Tabela
Panel z aktualną listą florystyczną.

- **Nagłówek** — pola *Lokalizacja / nr zdjęcia*, *Autor* i *Data* opisują punkt zbioru danych. Wartości są dołączane do eksportowanego pliku.
- **Tabela gatunków** — wyświetla grupę (NAC/MSZ/POR), akronim, nazwę łacińską, polską, przynależność do GRHG i GRRA, status ochronny oraz skalę częstości.
- **Skala częstości** — dla każdego gatunku można przypisać jedną z 5 wartości:
  - `+` — 1–3 stanowiska, skrajnie rzadki
  - `++` — kilka stanowisk, rzadki
  - `+++` — kilkanaście stanowisk, niezbyt częsty
  - `++++` — liczne stanowiska, częsty
  - `+++++` — masowo, pospolity
- **Usuwanie gatunków** — przycisk `✕` przy każdym wierszu usuwa gatunek z listy.
- **Wyczyść** — usuwa całą aktywną listę (z potwierdzeniem).

#### Eksport listy
- **⬇ Uproszczona** — eksportuje całą listę do jednego pliku CSV (wszystkie grupy). Kolumny: L.p., Nazwa polska, Nazwa łacińska, Ochrona, Częstość, Lokalizacja, Data, Autor.
- **⬇ Osobne** — otwiera menu wyboru grupy i eksportuje osobno: Rośliny naczyniowe (z kolumnami GRHG, GRRA, Rodzina), Mszaki lub Porosty.
- **✉ Wyślij CSV** — otwiera klienta poczty z całą listą wklejoną w treść wiadomości (temat i lokalizacja wypełniane automatycznie).
- **⬆ Lista** — importuje wcześniej zapisaną listę z pliku CSV. Dopasowuje gatunki po nazwie łacińskiej, polskiej lub akronimie.

### 🗄 Baza
Panel zarządzania wbudowaną bazą gatunków.

- **Stan bazy** — wyświetla liczbę gatunków w trzech grupach: naczyniowe, mszaki, porosty.
- **⬇ Eksport bazy (CSV)** — pobiera całą bazę do pliku CSV do weryfikacji lub uzupełnienia. Kolumny: `skr;lac;pl;rodz;grra;grhg;prot;grp`.
- **✉ Wyślij bazę** — wysyła bazę mailem (w treści wiadomości).
- **⬆ Importuj CSV** — wgrywa zaktualizowany plik CSV i scala go z istniejącą bazą (nowe rekordy są dodawane, istniejące aktualizowane).

---

## Format plików CSV

### Lista florystyczna
```
L.p.;Nazwa polska;Nazwa łacińska;Ochrona;Częstość;Lokalizacja;Data;Autor
```

### Baza gatunków
```
skr;lac;pl;rodz;grra;grhg;prot;grp
```
- `skr` — akronim 8-znakowy
- `lac` — nazwa łacińska
- `pl` — nazwa polska
- `rodz` — rodzina
- `grra` — grupa Raunkiaera
- `grhg` — grupa fitosocjologiczna (Hennekens & Groenendijk)
- `prot` — status ochronny
- `grp` — grupa: `v` (naczyniowe), `b` (mszaki), `l` (porosty)

---

## Dane i prywatność

Aplikacja przechowuje wszystkie dane lokalnie w przeglądarce (`localStorage`):
- bieżące zdjęcie fitosocjologiczne
- archiwum zapisanych zdjęć
- ewentualnie zmodyfikowana baza gatunków

Żadne dane nie są wysyłane na serwer. Wyczyszczenie pamięci przeglądarki spowoduje utratę danych — zalecany regularny eksport CSV.

---

## Technologie

- Czysty HTML/CSS/JavaScript — bez frameworków, bez zależności zewnętrznych
- PWA (manifest + meta tagi) — instalacja na ekranie głównym
- `localStorage` — przechowywanie danych offline
- Web Speech API — rozpoznawanie głosowe (Chrome/Android)
- Geolocation API — pobieranie współrzędnych GPS

---

## Powiązane narzędzia

**FastFrameFito** — siostrzana aplikacja do do terenowego wykonywania zdjęć fitosocjologicznych. Obie aplikacje korzystają ze wspólnej bazy gatunków w tym samym formacie CSV.

---

## Licencja

© 2026 Andrzej Rodziewicz — Arenaria sp. z o.o.

Udostępnione na licencji **CC BY-NC 4.0** (Creative Commons Uznanie autorstwa — Użycie niekomercyjne 4.0 Międzynarodowe).

Możesz swobodnie używać i modyfikować aplikację pod warunkiem podania autora i niekomercyjnego zastosowania. Komercyjne wykorzystanie wymaga pisemnej zgody autora.
