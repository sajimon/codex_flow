Pracujemy w trybie wielu agentów.

Celem jest wykonanie wszystkich milestone ze statusem `planned` z ROADMAP.md, z logicznym grupowaniem ich w batche, implementacją sekwencyjną, review po każdym batchu, poprawkami tylko jeśli są potrzebne oraz finalize/push tylko raz na końcu.

Użyj następujących subagentów:
- planning_agent
- implementation_agent
- review_agent
- operations_agent

Najpierw powołaj planning_agent.

Zadanie planning_agent:
- przeczytaj ROADMAP.md, spec.md i STATUS.md
- znajdź wszystkie milestone ze statusem `planned`
- pogrupuj milestone’y w batche po 2–3, jeśli są logicznie powiązane
- jeśli milestone jest duży, ryzykowny albo architektonicznie odrębny, zaplanuj go jako osobny batch
- ustal kolejność batchy zgodną z zależnościami z ROADMAP.md i spec.md
- nie implementuj kodu
- nie zmieniaj plików
- zwróć krótki plan batchy z uzasadnieniem

Po otrzymaniu planu batchy pokaż mi ten plan, a następnie przejdź przez batche sekwencyjnie.

Dla każdego batcha wykonaj poniższy cykl:

1. Powołaj implementation_agent.

Zadanie implementation_agent:
- realizuj milestone’y z bieżącego batcha sekwencyjnie
- dla każdego milestone przeczytaj jego cel, zakres i Definition of Done z ROADMAP.md
- implementuj wyłącznie zakres danego milestone’u
- nie dodawaj funkcji spoza milestone’u
- nie zmieniaj architektury bez wyraźnej potrzeby wynikającej z milestone’u
- jeśli wymaganie jest niejasne, doprecyzuj dokumentację albo zatrzymaj się z konkretnym pytaniem
- po każdym milestone uruchom adekwatne testy lub walidacje dla zmienionego zakresu
- nie wykonuj finalize
- nie wykonuj commit
- nie wykonuj push
- po zakończeniu batcha podsumuj:
  - wdrożone milestone’y
  - najważniejsze zmienione pliki
  - uruchomione testy lub walidacje
  - ewentualne ograniczenia albo ryzyka

2. Powołaj review_agent.

Zadanie review_agent:
- wykonaj niezależny przegląd zmian z bieżącego batcha
- sprawdź zgodność implementacji z ROADMAP.md, spec.md, STATUS.md i AGENTS.md, jeśli istnieje
- sprawdź, czy nie dodano zakresu spoza milestone’ów batcha
- sprawdź jakość kodu, prostotę rozwiązania, duplikację logiki, martwy kod i zbędne abstrakcje
- sprawdź sensowność testów i ryzyko regresji
- sprawdź, czy README.md, spec.md, ROADMAP.md albo STATUS.md wymagają aktualizacji z powodu wykonanych zmian
- nie edytuj żadnych plików
- nie wdrażaj poprawek
- jeśli nie ma problemów krytycznych, napisz dokładnie:
  Self-review zakończony – brak problemów krytycznych.
- jeśli są problemy, pogrupuj je według ważności:
  - Krytyczne
  - Ważne
  - Drobne
- do każdego problemu podaj konkretną rekomendowaną poprawkę

3. Jeśli review_agent wykryje realne problemy, powołaj implementation_agent ponownie.

Zadanie implementation_agent dla poprawek:
- wdroż wyłącznie poprawki wskazane przez review_agent
- nie dodawaj nowych funkcji
- nie rozszerzaj zakresu batcha
- nie wykonuj refaktoru większego niż konieczny do naprawy problemu
- jeśli jakaś poprawka wykracza poza zakres batcha, nie wdrażaj jej i zaznacz to w podsumowaniu
- po poprawkach wykonaj ograniczoną rewalidację zmienionego zakresu
- nie wykonuj finalize
- nie wykonuj commit
- nie wykonuj push

4. Jeśli były poprawki, powołaj review_agent ponownie.

Zadanie review_agent po poprawkach:
- sprawdź tylko problemy wcześniej wykryte oraz zmienione pliki
- potwierdź, czy problemy krytyczne zostały usunięte
- nie edytuj plików
- jeśli problemy krytyczne zostały usunięte, napisz:
  Self-review zakończony – brak problemów krytycznych.
- jeśli nadal istnieje problem krytyczny, zatrzymaj workflow i opisz blokadę

5. Przejdź do następnego batcha tylko wtedy, gdy:
- testy lub walidacje dla batcha przeszły
- review_agent nie zgłasza problemów krytycznych
- nie ma niejasności wymagających decyzji człowieka
- poprawki nie wykraczają poza zakres batcha

Jeśli którykolwiek warunek nie jest spełniony, zatrzymaj workflow i podsumuj blokadę. Nie przechodź do kolejnego batcha.

Po zakończeniu wszystkich batchy:

6. Powołaj review_agent do końcowej walidacji całości.

Zadanie review_agent:
- sprawdź całość zmian wykonanych w tym workflow
- sprawdź, czy wszystkie milestone ze statusem `planned`, które były objęte planem batchy, zostały zrealizowane
- sprawdź zgodność całości z ROADMAP.md, spec.md i STATUS.md
- sprawdź, czy dokumentacja wymaga aktualizacji przed finalizacją
- uruchom lub wskaż pełną walidację całości, jeśli projekt ją udostępnia
- nie edytuj plików
- zwróć wynik końcowej walidacji

7. Jeśli końcowa walidacja całości nie przejdzie, powołaj implementation_agent do poprawek.

Zadanie implementation_agent:
- wdroż wyłącznie poprawki wynikające z końcowej walidacji
- nie dodawaj nowego zakresu
- wykonaj adekwatną rewalidację
- po poprawkach wróć do review_agent po końcowe potwierdzenie

8. Gdy końcowa walidacja przejdzie, powołaj operations_agent.

Zadanie operations_agent:
- zaktualizuj ROADMAP.md zgodnie z rzeczywistym stanem ukończonych milestone’ów
- zaktualizuj STATUS.md, opisując aktualny stan projektu, istotne ograniczenia i następny sensowny krok
- zaktualizuj spec.md tylko wtedy, gdy wykonane zmiany realnie zmieniły ustalenia lub decyzje techniczne
- zaktualizuj README.md tylko wtedy, gdy zmienił się sposób użycia, uruchamiania, wymagania albo ważne zachowanie systemu
- nie zmieniaj kodu aplikacji
- przygotuj jeden commit dla całej paczki zmian
- wykonaj push tylko wtedy, gdy repo ma poprawnie skonfigurowany remote i stan jest gotowy
- nie wykonuj pustych commitów
- jeśli push zostanie pominięty, wyjaśnij dlaczego

Zasady globalne:
- używaj subagentów jawnie
- planning_agent planuje i nie implementuje
- implementation_agent implementuje i poprawia, ale nie finalizuje
- review_agent ocenia i nie edytuje plików
- operations_agent finalizuje, ale nie zmienia kodu aplikacji
- nie rozszerzaj zakresu milestone’ów
- nie zgaduj niejasnych wymagań
- nie wykonuj finalize, commit ani push po pojedynczym milestone ani po pojedynczym batchu
- minimalizuj zbędne pełne testy, ale zawsze wykonuj adekwatną walidację zmienionego zakresu
- zatrzymaj workflow przy problemie krytycznym, nieprzechodzących testach albo wymaganej decyzji człowieka

Na końcu podsumuj:
- plan batchy
- ukończone milestone’y
- wynik każdego batcha
- wyniki review
- wdrożone poprawki
- wynik końcowej walidacji
- zaktualizowane dokumenty
- status commit i push
