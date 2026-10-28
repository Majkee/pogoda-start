# Lumio TV: Pogoda

Kopia backendu i symulatora telewizorów Lumio do ćwiczeń z modułów 1 i 2: rejestr urządzeń, aktualizacje firmware'u (OTA) i katalog aplikacji. Ten sam serwer serwuje symulator telewizora z `tv/`. W tym repozytorium zmieniasz wszystko, także telewizor.

## Komendy

- Testy (całość): `./run_tests.sh` albo `run_tests.bat`. Bezpośrednio: `python -m unittest discover -s tests -t .` (na Windowsie zamiast `python` może być `py -3`).
- Jeden moduł testów: `python -m unittest tests.test_catalog -v`
- Serwer i telewizor: `./run_server.sh` albo `run_server.bat`, potem `http://localhost:8765/tv/?device=TV-001`. Opcje: `--port 9000`, `--reset` (przywraca stan urządzeń z `fixtures/`).

## Struktura

- `backend/` – pakiet Pythona: `api.py` (routing JSON), `server.py` (HTTP), `registry.py` (urządzenia), `ota.py` (aktualizacje), `catalog.py` (aplikacje), `storage.py` (pliki JSON).
- `tests/` – `unittest`. `tests/support.py` daje izolowany store i serwer na wolnym porcie.
- `fixtures/` – dane referencyjne (modele, wydania, aplikacje, urządzenia) i wektory testowe.
- `data/` – stan runtime serwera, nie commitujemy.
- `tv/` – klient telewizora (HTML, CSS, JavaScript bez bibliotek).

## Zasady

1. **Backend i telewizor możesz zmieniać.** Nowe endpointy, nowe pola, zmiany w `tv/` są w porządku.
2. **Python 3.9+ z biblioteką standardową.** Na komputerach szkoleniowych `pip` bywa zablokowany, więc nie dodawaj zależności bez wyraźnej potrzeby.
3. **Testy przechodzą.** Uruchamiaj je po zmianach. Przed zakończeniem pracy wszystkie muszą być zielone.

## Agent skills

### Issue tracker

Zgłoszenia i specyfikacje są lokalnymi plikami markdown w `.scratch/<feature>/`. See `docs/agents/issue-tracker.md`.

### Triage labels

Domyślne pięć ról (`needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`). See `docs/agents/triage-labels.md`.

### Domain docs

Single-context: `CONTEXT.md` i `docs/adr/` w katalogu głównym, tworzone w miarę potrzeby. See `docs/agents/domain.md`.
