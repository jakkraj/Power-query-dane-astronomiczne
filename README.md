# Power-query-dane-astronomiczne

Dane pochodzą z Gaia Data Release 3 i zostały poddane uproszczonemu czyszczeniu oraz selekcji. Analiza opiera się wyłącznie na jasności w paśmie G oraz paralaksie.

Nie uwzględniono:
– niepewności pomiarowych (np. parallax_error),
– ekstynkcji międzygwiazdowej,
– informacji barwowych (BP–RP).



Struktura zapytań Power Query

Projekt w Power Query jest podzielony logicznie na etapy. Każdy etap ma osobne zapytanie.

1) Import i czyszczenie danych

Zakres:

- wczytanie danych źródłowych,
- usunięcie pustych i oczywiście błędnych rekordów,
- ustawienie poprawnych typów danych,
- podstawowa walidacja (np. brak paralaksy równej 0).


2) Obliczenia

Zakres:

- obliczenie odległości w parsekach na podstawie paralaksy,
- obliczenie całkowitego ruchu własnego,
- obliczenie absolutnej jasności w paśmie G.

Przykładowe kolumny wynikowe: distance_pc, total_proper_motion, abs_mag_G

Na tym etapie nie ma jeszcze żadnych klas ani agregacji.


2.5) Zadanie poboczne – kwartyle i IQR

Zakres:

- policzenie kwartyli (Q1, Q3) dla wybranej zmiennej,
- wyznaczenie IQR,
- określenie granic dla obserwacji odstających.

Uwaga:
kwartyle mają sens tylko dla rozkładów w miarę ciągłych i jednowymiarowych, w przypadku danych silnie skośnych lub z błędami pomiarowymi należy zachować ostrożność.

3) Klasyfikacja i analiza

Zakres:

- przypisanie gwiazd do klas odległości (near / mid / far),
- przypisanie klas ruchu własnego (slow / moderate / fast),
- odfiltrowanie ekstremalnych wartości jasności,
- agregacja danych do prostych zestawień liczbowych.

Ten etap kończy się zapytaniem zgrupowanym i służy do analizy statystycznej, nie do wizualizacji pojedynczych obiektów.


4) Wykres HR (uproszczony)
Wykres ma charakter eksploracyjny i służy wizualnej ocenie struktury próby, a nie interpretacji astrofizycznej.
