# JustinClean — landing page audytu housekeepingowego

Prototyp niemieckojęzycznej strony dla usług housekeepingowych we Frankfurcie. Pokazuje ścieżkę od opisu problemów hotelu, przez ofertę bezpłatnego audytu na miejscu, do formularza kontaktowego.

**Status:** statyczne demo interfejsu. Formularze wyświetlają komunikaty potwierdzenia, ale nie przekazują zgłoszeń do firmy.

## Co można zobaczyć

- Sekcje korzyści, przykładowych referencji i czteroetapowego procesu współpracy.
- Główny formularz z danymi kontaktowymi i informacjami o obiekcie.
- Popup exit intent uruchamiany po wyjechaniu kursorem ponad stronę, z osobnym formularzem.
- Płynne przewijanie do sekcji i animacje elementów przy wejściu w obszar ekranu.
- Responsywny układ przygotowany w CSS.

## Technologia i struktura

Cała aplikacja znajduje się w [index.html](index.html): HTML opisuje sekcje strony, blok `<style>` zawiera wygląd i reguły responsywne, a końcowy `<script>` obsługuje interakcje. Nie ma bundlera, paczek npm, backendu ani bazy danych.

```text
.
├── index.html   # treść, style i logika przeglądarkowa
└── README.md
```

Zewnętrzna zależność to Google Fonts: DM Sans i Playfair Display. Bez internetu przeglądarka korzysta z fontów zastępczych. Ikony i dekoracje SVG są osadzone w dokumencie.

## Uruchomienie lokalne

Wymagane: Git, Python 3 i współczesna przeglądarka.

```sh
git clone https://github.com/dzwoniar/justinclean.git
cd justinclean
python -m http.server 8000
```

Otwórz [http://localhost:8000](http://localhost:8000). Na Windows zamiast `python` można użyć `py -3`. Serwer zatrzymasz przez `Ctrl+C`; instalacja zależności i krok budowania nie są potrzebne.

## Przepływ formularzy

Handler `leadForm` blokuje domyślną wysyłkę, zmienia stan przycisku i po 1,2 sekundy pokazuje potwierdzenie. `popupForm` również zmienia tylko interfejs, a następnie zamyka popup. Kod nie zawiera wywołania API ani zapisu zgłoszeń.

## Granice demonstracji i dalszy rozwój

- Główny formularz ma `novalidate`; obecny handler nie sprawdza wymaganych pól ani zgody przed pokazaniem sukcesu.
- Nazwa firmy w stopce i odnośniki do informacji prawnych pozostają placeholderami. Teksty o wynikach i referencjach są treścią prototypu, a nie zweryfikowanymi wynikami wdrożenia.
- Integrację formularzy należy dodać w handlerach `leadForm` i `popupForm`. Klucze usług powinny pozostać po stronie serwera.
- Obsługa przewijania obejmuje również linki `href="#"`; taki pusty cel wymaga poprawienia przed podłączeniem docelowych stron.

Repozytorium nie zawiera automatycznych testów. Przy zmianach warto sprawdzić układ na telefonie, przewijanie, otwieranie i zamykanie popupu oraz walidację formularzy po jej dodaniu.
