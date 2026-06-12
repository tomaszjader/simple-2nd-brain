---
name: create-simple-2nd-brain
description: Tworzy osobistą bazę wiedzy (drugi mózg) z folderami, schematem i gotowymi skillami. Oparty na wzorcu LLM Wiki Karpathy'ego. Działa dla każdego — inżynierów, twórców, badaczy, PMs, pisarzy. Użyj gdy ktoś chce zbudować bazę wiedzy, osobiste wiki lub drugi mózg z AI.
---

# Drugi Mózg

Większość narzędzi AI odpowiada od zera przy każdym zapytaniu. To narzędzie działa inaczej: model czyta źródła, kompiluje je do wiki i utrzymuje tę wiedzę w czasie. Każde nowe źródło aktualizuje wiele stron. Każda dobra odpowiedź trafia z powrotem do bazy. Wiedza narasta.

Człowiek dostarcza źródła i zadaje pytania. Model pisze, łączy, archiwizuje.

---

## Krok 1: Poznaj użytkownika

Odczytaj `references/questions.md` i zadaj użytkownikowi kolejno każdy blok pytań z tego pliku. Każdy blok to jedno wejście — jeden blok, jedna odpowiedź.

- Odpowiedzi na **P1** (kontekst) zapamiętaj jako `{about_odpowiedzi}`.
- Odpowiedzi na **P2** (styl komunikacji) zapamiętaj jako `{styl_komunikacji}` — wyciągnij konkretne preferencje (np. „bezpośrednio, bez agresji", „strukturalnie — bullety", „zwięźle", „swobodny ton", „wymagająco").

---

## Krok 2: Ustal temat i lokalizację

Jeśli `$ARGUMENTS` nie jest pusty — użyj go jako tematu. Zamień na slug (małe litery ASCII, spacje na myślniki, usuń znaki specjalne i polskie litery: ą→a, ę→e, ś→s, ź/ż→z, ó→o, ć→c, ł→l, ń→n). Przejdź do pytań 2 i 3 poniżej.

Jeśli `$ARGUMENTS` jest pusty — zadaj użytkownikowi kolejno:

1. „O czym ma być ta baza wiedzy?"
2. „Co 3–5 rzeczy stale śledzisz w tym obszarze?"
3. „Jakie źródła tu wrzucasz? (artykuły, notatki, dokumentacja, transkrypty, logi...)"

Zapamiętaj odpowiedzi jako: `{temat}`, `{zainteresowania}`, `{typy_źródeł}`.

4. „Gdzie chcesz utworzyć bazę?"
   - **w bieżącym folderze** → `{slug}` = `.` (baza tworzona bezpośrednio tutaj, bez podfolderu)
   - **w nowym podfolderze** → zapytaj: „Jak nazwać folder?" i użyj tej nazwy jako `{slug}`

Zapamiętaj odpowiedź jako `{slug}`.

**Sprawdź czy baza już istnieje:** jeśli lokalizacja `{slug}` już zawiera `AGENTS.md` — poinformuj użytkownika i zapytaj czy chce kontynuować istniejącą bazę (zakończ skill) czy utworzyć nową (kontynuuj).

---

## Krok 3: Utwórz strukturę

Ustal `{katalog_bazowy}`:
- jeśli `{slug}` = `.` → `{katalog_bazowy}` = `.`
- w przeciwnym razie → `{katalog_bazowy}` = `{slug}`

```bash
mkdir -p {katalog_bazowy}/raw {katalog_bazowy}/wiki {katalog_bazowy}/outputs {katalog_bazowy}/skills
```

Skopiuj skille z tego repo do nowej bazy (skille zawsze trafiają do `skills/`):
```bash
cp -r references/skills/2nd-brain-ingest {katalog_bazowy}/skills/
cp -r references/skills/2nd-brain-query {katalog_bazowy}/skills/
cp -r references/skills/2nd-brain-lint {katalog_bazowy}/skills/
```

Poinformuj użytkownika:
- **Skille** są gotowe w `skills/` — aby z nich korzystać, poproś swojego asystenta AI o ich zainstalowanie (np. „zainstaluj skille z folderu skills/"). Większość narzędzi AI (Claude Code, Cursor, Codex) obsługuje to automatycznie.
- **Obsidian** — linki `[[strona]]` stają się klikalne, widok grafu pokazuje całą bazę.
- **git** — `git init && git add . && git commit -m "setup"` daje historię i możliwość cofania.

---

## Krok 4: Zapisz `{slug}/AGENTS.md`

Użyj dzisiejszej daty w formacie RRRR-MM-DD wszędzie gdzie pojawia się `{data}`.

Przed zapisem pliku — przetworz zebrane odpowiedzi:

**`{o_uzytkowniku}`** — na podstawie P1 napisz 2–4 zdania opisujące kim jest użytkownik: jego rolę, kontekst pracy i co jest dla niego ważne. Pisz w trzeciej osobie, konkretnie, bez ogólników. Przykład: „Senior engineer w startupie B2B SaaS (50 osób). Odpowiada za architekturę backendu i onboarding nowych devów. Interesuje go głównie skalowalność i dług techniczny."

**`{zasady_komunikacji}`** — na podstawie P2 wygeneruj listę konkretnych zasad jak model ma się zachowywać. Każda zasada to jedno zdanie zaczynające się od czasownika. Przykład: „Mów wprost, bez wstępów i podsumowań.", „Używaj bulletów i nagłówków zamiast długich akapitów.", „Przy krytyce nie łagodź — podaj problem i co konkretnie zmienić.", „Odpowiadaj zwięźle; szczegóły tylko gdy użytkownik dopyta.". Wygeneruj tyle zasad ile wynika z odpowiedzi — nie skracaj ani nie rozszerzaj sztucznie.

Użyj poniższego bloku jako `{blok_skilli}` — wszystkie narzędzia obsługują skille przez slash komendy:

```
Używaj tych skilli zamiast ręcznych poleceń:

| Skill | Kiedy używać |
|-------|-------------|
| `/2nd-brain-ingest [nazwa_pliku]` | Po dodaniu pliku do `raw/` — przetwarza źródło i eksploruje nowe powiązania |
| `/2nd-brain-query [pytanie]` | Gdy chcesz się czegoś dowiedzieć z bazy |
| `/2nd-brain-lint` | Co 2–4 tygodnie lub gdy baza mocno urosła — sprawdza jakość wiki |

Skille znajdziesz w `skills/`. Jeśli nie są jeszcze zainstalowane, poproś asystenta AI: „zainstaluj skille z folderu skills/".
```

```markdown
# Baza wiedzy: {temat}

## Struktura
- `raw/` — źródła. Niezmienne. Nigdy nie modyfikuj tych plików.
- `wiki/` — skompilowana wiedza. Należy wyłącznie do modelu.
- `outputs/` — raporty i odpowiedzi warte zachowania. Jeśli wynik nadaje się na stronę wiki — przenieś go.
- `skills/` — skille do obsługi bazy (2nd-brain-ingest, 2nd-brain-query, 2nd-brain-lint).

## Zasady wiki
- Każda strona to osobny plik `.md` w `wiki/`.
- Nagłówek YAML każdej strony: `title`, `created`, `last_updated`, `source_count`, `status`.
- Pierwsze zdanie strony to streszczenie jednym akapitem.
- Linkuj agresywnie: `[[nazwa-strony]]`. Powiązania są równie ważne co treść.
- Cytuj każde twierdzenie: `[Źródło: plik.md]`.
- Przy sprzeczności: nie nadpisuj. Zanotuj oba twierdzenia, oba źródła, zaznacz które jest nowsze.

## Indeks i dziennik
- `wiki/index.md` — spis wszystkich stron, jeden opis na linię, pogrupowany tematycznie. Aktualizuj po każdym pobraniu. Przed odpowiedzią zawsze sprawdź indeks.
- `wiki/log.md` — tylko do dopisywania. Format: `## [RRRR-MM-DD] akcja | opis`. Akcje: `ingest`, `query`, `lint`, `explore`.

## Dostępne skille
{blok_skilli}

## Użytkownik
{o_uzytkowniku}

Zainteresowania w tym obszarze: {zainteresowania}

## Jak się komunikować
{zasady_komunikacji}

## Czego się spodziewać w źródłach
Typy źródeł w tej bazie: {typy_źródeł}. Dopasuj poziom szczegółowości i język odpowiedzi do tego kontekstu.
```

---

## Krok 5: Utwórz `wiki/index.md` i `wiki/log.md`

`{slug}/wiki/index.md`:
```markdown
# Indeks

_Aktualizacja: {data}_

Brak stron. Dodaj źródła do `raw/` i użyj `/ingest [nazwa_pliku]`.
```

`{slug}/wiki/log.md`:
```markdown
# Dziennik

## [{data}] init | Baza utworzona
Temat: {temat}. Gotowe na pierwsze źródła.
```

---

## Krok 6: Wyświetl podsumowanie

```
Baza gotowa: {slug}/

Struktura:
  raw/        ← tu wrzucaj źródła
  wiki/        ← tu rośnie wiedza
  outputs/     ← tu lądują raporty
  skills/      ← skille (2nd-brain-ingest, 2nd-brain-query, 2nd-brain-lint)

Co dalej:
1. Wrzuć dowolny plik do raw/.
2. Użyj /ingest [nazwa_pliku] — model zbuduje wiki.
3. Zadawaj pytania przez /query [pytanie].
4. Co jakiś czas: /lint — sprawdzi jakość i spójność bazy.

Pamiętaj: otwieraj nową rozmowę z katalogu {slug}/ żeby model widział AGENTS.md i skille.
```
