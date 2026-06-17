---
name: 2nd-brain-lint
description: Sprawdza jakość wiki — sprzeczności, sieroty, braki cytowań, nieaktualne strony. Użyj co 2–4 dni lub gdy baza mocno urosła.
---

Przeczytaj plik konfiguracyjny bazy: `AGENTS.md` w bieżącym katalogu.

Przejrzyj wszystkie strony w `wiki/` i sprawdź każdy z poniższych punktów:

**Sprzeczności**
Znajdź twierdzenia na różnych stronach które sobie przeczą. Dla każdej sprzeczności: podaj obie strony, oba twierdzenia, oba źródła, wskaż które jest nowsze.

**Nieaktualne twierdzenia**
Znajdź strony z `last_updated` starszym niż 60 dni które mogły się zdezaktualizować w świetle nowszych źródeł.

**Strony bez linków przychodzących (sieroty)**
Znajdź strony w `wiki/` do których żadna inna strona nie linkuje przez `[[nazwa]]`.

**Pojęcia bez własnej strony**
Znajdź `[[linki]]` w wiki które wskazują na nieistniejące strony. To są luki do wypełnienia.

**Twierdzenia bez cytowania**
Znajdź konkretne fakty, liczby lub twierdzenia które nie mają `[Źródło: ...]`.

**Indeks vs rzeczywistość**
Sprawdź czy `wiki/index.md` zawiera wszystkie istniejące strony. Dodaj brakujące.

---

Zapisz wynik jako `wiki/lint-[RRRR-MM-DD].md` z sekcjami per kategoria. Każda pozycja: strona, opis problemu, propozycja naprawy.

Na końcu zaproponuj 3 źródła które wypełniłyby największe luki.

Dopisz do `wiki/log.md`: `## [RRRR-MM-DD] lint | [liczba problemów] problemów — szczegóły w wiki/lint-[data].md`.
