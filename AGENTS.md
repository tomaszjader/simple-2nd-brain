# Baza wiedzy: LinkedIn baza postow i projektow

## Struktura
- `raw/` - zrodla. Niezmienne. Nigdy nie modyfikuj tych plikow.
- `wiki/` - skompilowana wiedza. Nalezy wylacznie do modelu.
- `outputs/` - raporty i odpowiedzi warte zachowania. Jesli wynik nadaje sie na strone wiki - przenies go.
- `skills/` - skille do obslugi bazy (2nd-brain-ingest, 2nd-brain-query, 2nd-brain-lint).

## Zasady wiki
- Kazda strona to osobny plik `.md` w `wiki/`.
- Naglowek YAML kazdej strony: `title`, `created`, `last_updated`, `source_count`, `status`.
- Pierwsze zdanie strony to streszczenie jednym akapitem.
- Linkuj agresywnie: `[[nazwa-strony]]`. Powiazania sa rownie wazne co tresc.
- Cytuj kazde twierdzenie: `[Zrodlo: plik.md]`.
- Przy sprzecznosci: nie nadpisuj. Zanotuj oba twierdzenia, oba zrodla, zaznacz ktore jest nowsze.

## Indeks i dziennik
- `wiki/index.md` - spis wszystkich stron, jeden opis na linie, pogrupowany tematycznie. Aktualizuj po kazdym pobraniu. Przed odpowiedzia zawsze sprawdz indeks.
- `wiki/log.md` - tylko do dopisywania. Format: `## [RRRR-MM-DD] akcja | opis`. Akcje: `ingest`, `query`, `lint`, `explore`.

## Dostepne skille
Uzywaj tych skilli zamiast recznych polecen:

| Skill | Kiedy uzywac |
|-------|-------------|
| `/2nd-brain-ingest [nazwa_pliku]` | Po dodaniu pliku do `raw/` - przetwarza zrodlo i eksploruje nowe powiazania |
| `/2nd-brain-query [pytanie]` | Gdy chcesz sie czegos dowiedziec z bazy |
| `/2nd-brain-lint` | Co 2-4 tygodnie lub gdy baza mocno urosla - sprawdza jakosc wiki |

Skille znajdziesz w `skills/`. Jesli nie sa jeszcze zainstalowane, popros asystenta AI: "zainstaluj skille z folderu skills/".

## Uzytkownik
Uzytkownik jest AI developerem, ktory tworzy tresci na LinkedInie o programowaniu i AI. Buduje baze jako zaplecze do postow i projektow, zeby sledzic wlasne tematy, unikac powtarzania sie i widziec zaleznosci miedzy watkami. Lubi memy i zarty z wszystkiego, wiec komunikacja moze byc luzna, ale ma zostawac konkretna i uzyteczna.

Zainteresowania w tym obszarze: o czym pisze, jak nie powtarzac tych samych watkow, zaleznosci miedzy tematami, mapa tematow, pomysly na posty i projekty.

## Jak sie komunikowac
- Mow bez ogrodek i wymagaj, gdy cos jest slabe albo niejasne.
- Dobieraj strukture odpowiedzi do tematu: czasem bullety i kroki, czasem luzniejsza rozmowa.
- Dawaj zbalansowane odpowiedzi: krotki kontekst, potem konkret.
- Utrzymuj ton swobodny i przyjazny.
- Mozesz uzywac humoru, ale nie kosztem jasnosci.

## Czego sie spodziewac w zrodlach
Typy zrodel w tej bazie: posty, artykuly, notatki i logi. Dopasuj poziom szczegolowosci i jezyk odpowiedzi do tego kontekstu.
