---
name: 2nd-brain-ingest
description: Przetwarza jedno źródło z raw/ do wiki, a następnie eksploruje nowe powiązania w bazie. Użyj za każdym razem gdy dodajesz nowy plik.
---

Przeczytaj plik konfiguracyjny bazy: `AGENTS.md` w bieżącym katalogu.

Plik do przetworzenia: `raw/$ARGUMENTS`

---

## Faza 1: Przetwarzanie źródła

1. Przeczytaj całe źródło `raw/$ARGUMENTS`.
2. Omów z użytkownikiem 3–5 kluczowych wniosków. Poczekaj na odpowiedź — może wskazać co jest ważne.
3. Utwórz stronę streszczenia w `wiki/`. Nagłówek YAML: `title`, `created` (dzisiejsza data RRRR-MM-DD), `last_updated`, `source_count: 1`, `status: draft`. Pierwsze zdanie to jeden akapit streszczenia. Linkuj agresywnie do istniejących stron `[[nazwa]]`. Cytuj twierdzenia: `[Źródło: $ARGUMENTS]`.
4. Przeczytaj `wiki/index.md`. Dodaj nową stronę do indeksu pod odpowiednią grupą tematyczną.
5. Przeczytaj istniejące strony wiki powiązane tematycznie. Zaktualizuj je o nową wiedzę i dodaj linki zwrotne do nowej strony.
6. Jeśli nowe źródło przeczy czemuś w wiki — nie nadpisuj. Zanotuj oba twierdzenia, oba źródła, zaznacz które jest nowsze.
7. Dopisz do `wiki/log.md`: `## [RRRR-MM-DD] ingest | $ARGUMENTS — [jedno zdanie co wniosło]`.

---

## Faza 2: Eksploracja powiązań

Po przetworzeniu źródła automatycznie sprawdź czy otworzyło nowe połączenia w bazie:

1. Porównaj nową stronę z `wiki/index.md` — znajdź strony które tematycznie na siebie wpływają ale nie mają jeszcze linków.
2. Jeśli znajdziesz silne powiązanie — zaproponuj użytkownikowi:
   - dodanie linku `[[nazwa]]` między stronami, lub
   - utworzenie nowej strony syntezy, lub
   - oznaczenie jako luki do wypełnienia kolejnym źródłem.
3. Wdróż zatwierdzone działania i zaktualizuj `wiki/log.md`: `## [RRRR-MM-DD] explore | [co odkryto i co zrobiono]`.

Jeśli baza ma mniej niż 3 strony — pomiń Fazę 2.

---

Na koniec pokaż: które strony wiki utworzyłeś, które zaktualizowałeś, jakie nowe powiązania znalazłeś.
