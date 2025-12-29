---
description: Generuje z PRD nowe pliki spec.md i ROADMAP.md
---

Na podstawie pliku `PRD.md`:

1. Wypełnij treścią istniejący plik `spec.md`, korzystając z jego OBECNEJ struktury.
2. Nie zmieniaj nagłówków, nazw sekcji ani kolejności w `spec.md`.
3. Uzupełnij każdą sekcję na poziomie wysokim (bez detali implementacyjnych).
4. Jeśli którejś sekcji nie da się uzupełnić na podstawie PRD:
   - zostaw krótką notatkę `TODO` z opisem brakującej informacji.

Dodatkowo:
5. Zaproponuj roadmapę w formie jasno nazwanych milestone’ów.
6. Każdy milestone ma mieć:
   - cel
   - kryteria „Definition of Done”
   - krótki opis zakresu

Wynik zapisz do plików:
- `spec.md` — wypełniona specyfikacja wysokiego poziomu
- `ROADMAP.md` — roadmapa z milestone’ami

Zasady:
- Nie zmieniaj struktury `spec.md`.
- Nie zmieniaj kodu.
- Nie dodawaj zależności ani decyzji implementacyjnych bez wyraźnego uzasadnienia w `## Decyzje techniczne`.
