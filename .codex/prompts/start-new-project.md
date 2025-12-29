---
description: start nowego projektu, tworzenie spec.md, ROADMAP.md  i STATUS.md
---

Utwórz pliki `spec.md`, `ROADMAP.md` i `STATUS.md` jako szablony w ustalonym układzie.

`spec.md` ma zawierać DOKŁADNIE poniższy szablon.
Nie zmieniaj nazw sekcji, nagłówków ani kolejności.
Nie uzupełniaj treści merytorycznej.

====================
# Specyfikacja techniczna

## Cel
Krótki opis celu aplikacji:
- jaki problem rozwiązuje
- dla kogo
- w jakim zakresie (co jest poza zakresem)

---

## Zakres funkcjonalny (high-level)
Opis funkcjonalności na wysokim poziomie:
- kluczowe use-case’i
- główne przepływy użytkownika
- czego aplikacja **nie** robi

Bez wchodzenia w szczegóły implementacyjne.

---

## Architektura i przepływ danych
Opis architektury na poziomie koncepcyjnym.

1. Główne komponenty systemu
2. Przepływ danych między komponentami
3. Granice odpowiedzialności

---

## Komponenty techniczne
Lista kluczowych komponentów technicznych i ich odpowiedzialności.

---

## Decyzje techniczne
Jawne decyzje techniczne wraz z uzasadnieniem.

Każda decyzja powinna zawierać:
- Decyzja:
- Uzasadnienie:
- Konsekwencje:

---

## Jakość i kryteria akceptacji
Wspólne wymagania jakościowe dla całego projektu.

---

## Zasady zmian i ewolucji
- zmiany funkcjonalne → aktualizacja `ROADMAP.md`
- zmiany architektoniczne → aktualizacja tej specyfikacji
- nowe zależności → wpis do `## Decyzje techniczne`
- refactory tylko w ramach aktualnego milestone’u

---

## Powiązanie z roadmapą
- Szczegóły milestone’ów i ich statusy znajdują się w `ROADMAP.md`.

---

## Status specyfikacji
- Data utworzenia:
- Ostatnia aktualizacja:
- Aktualny zakres obowiązywania:

====================

`ROADMAP.md` ma zawierać:
# Roadmapa (milestones)

## Milestone <numer>: <nazwa> (<status>)
Cel:
Definition of Done:
Zakres:

Nie uzupełniaj treści merytorycznej.

`STATUS.md` ma zawierać:
# Aktualny stan
- co działa:
- co jest skończone:
- co jest następne:

Nie uzupełniaj treści merytorycznej.
Nie zmieniaj kodu.
