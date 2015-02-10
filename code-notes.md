# Spis rzeczy

1. Wstęp
2. CleanCode w OOP na przykładzie (Args)
3. "Refaktoring to functional" (TM Hadi Hariri)
4. Przenikanie FP do C# - przegląd zmian w języku
5. Porównanie C# 6 vs. F#
6. Monady
7. FP in a nutshell (fold)
8. Args w F#
9. Podsumowanie

# DEMO: Args

- dobre OOP, unit testy, top-down, krótkie metody, dobre nazwy, SRP, łatwo rozszerzalny
- Alt-Enter i do przodu!
- lambdy i factory method (na górę kod, który będzie rozszerzany)
- ``Get<T>`` zamiast GetDouble... (nadal nie podoba mi się object)
- 1 zamiast 5 "zmiennych" instancji
- "zmienna", a raczej wartość bo się nie zmienia
- pure functions
- z pewnym kosztem: dłuższe deklaracje (brak type inference)
- marshaller też jest w zasadzie funkcją
- IEnumerator jedynym stanem
- "ufunkcyjnienie" rozwiązania obiektowego: czyste funkcje, brak stanu

# DEMO: Playground.fs

- bądźmy maksymalistami
- ciegiełkami są funkcje
- ważne są typy
- automatyczna generalizacja
- składamy funkcje w różne kombinacje: mamy różne operatory
- proste sklejanie
- "forward pipe" - fluent syntax
- inny "proces twórczy": REPL, z którego później krystalizują się test
- to też TDD, bo chodzi o szybki pętlę zwrotną

# DEMO: Args.fs

- unia dyskryminująca (enum++) ErrorCode
- monada ROP (Scott Wlaschin) zamiast wyjątków
 - rozwinięcie tego co zrobił Uncle Bob (Exception -> ArgException(ErrorCode) -> Failure(ErrorCode))
 - dokumentuje wszystko co może pójść nie tak
 - more explicit, pokazuje ukryte wymagania
 - type safe (nie postawimy try/catch w złym miejscu)
 - ułatwia testowanie
 - ułatwia tłumaczenie etc.
- komponuje funkcję w ten sposób, że głównym torem sukces, a drugim porażka (skrót, pomija kolejne wywołania)
- deklaracja typów (opcjonalne, komputer sobie bez nich poradzi)
 - w C#/Java tworzymy zmienne instancji, aby uniknąć przepychania przez argumenty
- ? Script.fsx
- oddzielone parsowanie schematu od parsowania argumentów (Args nie był pisany w TDD)
- |> jak LINQ - porównać kod
- ? inny "proces twórczy": REPL
- ? StringListMarshaller - praca domowa z książki
- ? ValidArgument - active pattern
- ? git checkout bang
