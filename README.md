# Pogoda

Repozytorium do ćwiczeń z modułów 1 i 2. Budujesz w nim tę samą małą aplikację trzy razy, za każdym razem inną metodą pracy z agentem, i porównujesz wyniki.

Treść zadań jest na stronie z ćwiczeniami. Tu jest tylko punkt startowy: puste repozytorium ze skillami.

## Start (5 minut)

Potrzebujesz gita i agenta (Claude Code albo Cline). Stack wybierasz sam.

1. Sklonuj repozytorium albo rozpakuj ZIP od prowadzącego (ZIP zawiera katalog `.git` i tag `start`).
2. Sprawdź tag startowy: `git tag` powinno wypisać `start`.
3. Otwórz agenta w katalogu repozytorium i wpisz `/`. Na liście powinny być `/grilling` i `/grill-with-docs`.

## Gałęzie

Każda wersja aplikacji powstaje na osobnej gałęzi, zawsze od tagu `start`. Dzięki temu wszystkie wersje zostają w repozytorium i można je porównać.

| Zadanie | Gałąź | Polecenie |
| --- | --- | --- |
| 1. Vibe coding | `vibe` | `git switch -c vibe start` |
| 2. Grilling | `grill` | `git switch -c grill start` |
| 3. Grill with docs | `docs` | `git switch -c docs start` |

Przed przejściem do kolejnego zadania zacommituj wszystko na bieżącej gałęzi (`git add -A` i `git commit`).

Porównanie dwóch wersji:

```bash
git diff vibe grill --stat
```

Każda wersja może działać na innym porcie, więc możesz otworzyć je obok siebie (np. w dwóch kopiach katalogu albo przez `git worktree add ../pogoda-vibe vibe`).

## Skille

Skille Matta Pococka (repozytorium `mattpocock/skills`) są w repozytorium w zamrożonej wersji, w `.claude/skills/` i `.cline/skills/`. Niczego nie instalujesz.

| Skill | Do czego |
| --- | --- |
| `/grilling` | wywiad, który doprecyzowuje plan przed pisaniem kodu |
| `/grill-with-docs` | ten sam wywiad, ale zapisuje też słownik pojęć (`CONTEXT.md`) i decyzje (`docs/adr/`) |
| `/domain-modeling` | słownik domeny i decyzje architektoniczne (używany przez `/grill-with-docs`) |
| `/to-spec` | specyfikacja z dotychczasowej rozmowy |
| `/to-tickets` | podział specyfikacji na tickety |
| `/implement` | implementacja ticketu |
| `/tdd` | red → green → refactor |
| `/diagnosing-bugs` | pętla diagnozy błędu |
| `/code-review` | review zmian od wskazanego commita lub tagu |

Zgłoszenia, tickety i specyfikacje są plikami markdown w `.scratch/<feature>/`.

## Powrót do startu

`git switch -c <nowa-gałąź> start` zaczyna od zera bez kasowania innych wersji. Nie używaj `git reset --hard` na gałęzi z wersją, którą chcesz jeszcze porównać.
