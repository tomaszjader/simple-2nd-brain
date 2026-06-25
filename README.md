# Drugi Mózg - Osobista Baza Wiedzy

To jest moja osobista baza wiedzy w stylu "second brain". Zamiast zaczynać od zera przy każdym pytaniu, AI buduje i utrzymuje lokalne wiki na podstawie moich materiałów źródłowych.

## O tej bazie

Baza skupia się na tematach związanych z:
- **AI i Agentami**: MCP, LangChain, Google ADK, prompt engineering
- **Automatyzacja**: n8n, workflow, narzędzia no-code
- **Projekty**: pomysły na aplikacje, nauka angielskiego, automatyzacje osobiste
- **Treści**: posty z LinkedIn, notatki z kursów i szkoleń

## Jak otworzyć bazę w Obsidianie

1. Otwórz aplikację Obsidian.
2. Wybierz `Open folder as vault`.
3. Wskaż ten katalog jako vault.

Możesz przeglądać wiki, korzystać z linków `[[wewnętrznych]]` i używać widoku grafu.

## Struktura bazy

```text
lama-isurence/
  ├── raw/         <- surowe materiały źródłowe (obecnie puste)
  ├── wiki/        <- główna warstwa wiedzy (50+ stron)
  ├── outputs/     <- raporty, odpowiedzi i syntezy
  ├── skills/      <- skille do pracy z bazą
  └── AGENTS.md    <- zasady działania i konfiguracja
```

## Dostępne skille

W katalogu `skills/` znajdziesz trzy sub-skille do codziennej pracy z wiedzą:

### 1. `2nd-brain-ingest`
Służy do dodawania nowych źródeł do bazy. Wrzucasz plik do `raw/`, a skill analizuje treść, aktualizuje wiki i tworzy powiązania.

### 2. `2nd-brain-query`
Służy do zadawania pytań na podstawie zawartości bazy. Przeszukuje `wiki/` i przygotowuje odpowiedzi oparte na zgromadzonych materiałach.

### 3. `2nd-brain-lint`
Służy do utrzymania jakości bazy. Sprawdza wiki pod kątem martwych linków, niespójności i sugeruje ulepszenia.

## Jak korzystać z bazy

1. **Dodawaj nowe materiały** do folderu `raw/`
2. **Uruchamiaj `2nd-brain-ingest`** żeby włączyć je do wiki
3. **Zadawaj pytania** przez `2nd-brain-query`
4. **Regularnie uruchamiaj `2nd-brain-lint`** dla utrzymania jakości

## Zawartość wiki

Baza zawiera obecnie 50+ stron z wiedzą o:
- Agentach AI i narzędziach (MCP, LangChain, Google ADK)
- Automatyzacji (n8n, workflow)
- Pomysłach na projekty (aplikacje, narzędzia)
- Treściach z LinkedIn i kursów
- Logu i raportach z lintowania

Ostatnia aktualizacja: 2026-06-23
