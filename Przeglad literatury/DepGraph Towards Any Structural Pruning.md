https://arxiv.org/pdf/2301.12900
Praca proponuje uniwersalne rozwiązanie pozwalające na strukturalny pruning dowolnego modelu niezależnie od architektury. Problem ze strukturalnym pruningiem polega na tym, że usuwając kanał w jednej warstwie musimy zmienić wejście do następnej co jest szczególnie problematyczne dla części architektur. 
Rozwiązaniem tego problemu ma być DepGraph, czyli metoda automatycznego modelowania zależności między parametrami w dowolnej architekturze.
# DepGraph
Działa w oparciu o analizowanie przepływu danych i buduje graf zależności. Jeżeli chcemy usunąć dany filtr DepGraph wskazuje wszystkie inne parametry w sieci, które muszą zostać usunięte razem z filtrem aby zachować spójność matematyczną modelu.
## Proces budowania grafu
1. Każda warstwa w sieci (Conv, Linear, BatchNorm) jest traktowana jako węzeł w grafie. Algorytm nie patrzy tylko na warstwy ale też na zależności między ich wejściami i wyjściami.
2. Mapowanie relacji. Autorzy definiują dwa główne ich typy
	1. Zależność wewnątrz-warstwowa: Określa, jak zmiana liczby kanałów wejściowych wpływa na kanały wyjściowe w obrębie tej samej warstwy
	2. Zależności międzwarstwowe: Określa w jaki sposób kanały wyjściowe warstwy A są zależne od kanałów wejściowych warstwy B
3. Grupowanie parametrów. Budowa odbywa się poprzez propagację zależności:
	1. Inicjalizacja: każdy parametr zaczyna we własnej grupie
	2. Śledzenie przepływu: Algorytm przechodzi przez graf obliczeniowy sieci. jeśli napotka operacje która wymusza taką samą liczbę kanałów, łączy te parametry w jedną wspólną **grupę zależności**
	3. Obsługa operacji specjalnych: Mapuje operacje specjąlne takie jak split, view/reshape, transpose, np mapując ktore indeks wagi po operacji reshape odpowiadają któremu indeksowi przed operacją.
Po zbudowaniu grafu pruning robi się prosty.
- Wybieramy parametr do usunięcia
- DepGraph sprawdza do jakiej grupy zależności należy ten parametr.
- Wszystkie parametry z grupy usuwamy na raz.

#Pruning #Y2023