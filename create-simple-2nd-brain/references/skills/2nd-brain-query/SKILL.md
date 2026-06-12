---
name: 2nd-brain-query
description: Odpowiada na pytanie korzystając z wiki. Użyj gdy chcesz się czegoś dowiedzieć z bazy wiedzy.
---

Przeczytaj plik konfiguracyjny bazy: `AGENTS.md` w bieżącym katalogu.

Pytanie: $ARGUMENTS

Wykonaj kolejno:

1. Przeczytaj `wiki/index.md`. Zidentyfikuj strony trafne dla pytania.
2. Przeczytaj te strony. Podążaj za linkami `[[nazwa]]` po dodatkowy kontekst — maksymalnie 2 poziomy głębiej.
3. Odpowiedz na pytanie z odniesieniami do konkretnych stron wiki (`[wiki/nazwa-strony.md]`).
4. Dobierz format odpowiedzi:
   - Pytanie faktyczne → krótka odpowiedź z cytatami
   - Porównanie → tabela markdown
   - Przegląd tematu → struktura z nagłówkami
   - Analiza → briefing: stan obecny / kluczowe napięcia / otwarte pytania / rekomendacje
5. Zapytaj użytkownika: „Czy zapisać tę odpowiedź do wiki?" Jeśli tak — utwórz stronę w `wiki/`, zaktualizuj `wiki/index.md` i dopisz wpis do `wiki/log.md`: `## [RRRR-MM-DD] query | [pytanie] — zapisano do wiki/[nazwa-strony].md`.
