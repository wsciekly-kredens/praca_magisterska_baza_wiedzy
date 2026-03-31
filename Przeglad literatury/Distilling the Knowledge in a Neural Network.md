> https://arxiv.org/pdf/1503.02531

Praca opisuje sposób destylacji wiedzy z większego modelu.
Opisany sposób opiera się na wytrenowaniu dużego modelu (nauczyciela) i przekazanie jego **logitów** (to w tym wypadku wyjścia po softmaxie ze zwiększoną temperaturą) jako target dla mniejszej sieci. W ten sposób mniejsza sieć uczy się nie tyle predykcji i poprawnego rozpoznawania wyników co dokładnego odtwarzania wyników większej sieci.

Owe logity mają formę rozkładu i kopiowania tego rozkładu uczy się mniejsza sieć. Nazywane jest to **soft target** (soft target oznacza właśnie zwiększenie temperatury co przekłada się na gładszy rozkład).

W pracy wykorzystano zmodyfikowaną funkcję softmax
$$q_i = \frac{exp(z_i/T)}{\sum_jexp(z_j/T)}$$
Dodano do niej współczynnik $T$ który określa temperaturę modelu. Ustawienie $T=1$ daje nam standardowy softmax. Dla rosnącego $T$ dostajemy gładszy rozkład prawdopodobieństwa przynależności do danej klasy. 

# Trening modelu
Trening odbywa się z wykorzystaniem funkcji softmax przy standardowym ($T=1$) ustawieniu temperatury. Dla tak nauczonego modelu do trenowania modelu do otrzymania danych do treningu mniejszego modelu zwiększa się wartość temperatury, co przekłada się na lepszy wgląd do tego jak siec nauczyciela rozumuje. Otrzymany w ten sposób gładszy rozkład pozwala również na uchwycenie podobieństwa między instancjami danych klas. Praca opierała się na trenowaniu modelu w rozpoznawaniu cyfr na zbiorze MINIST. Dla najlepszych sieci (dokładność dużo ponad 90%) produkowany przez nie rozkład jest bardzo jednoznaczny, model zazwyczaj ma dużą pewność co do klasy (typu 0,9 co oznacza że na pozostałe 9 klas zostaje do rozdysponowania 0,1) obrazu co produkuje rozkład tylko z jednym ekstremum. Uniemożliwia to wyuczenie zależności, że 4 może w niektórych sytuacjach przypominać 9. Gładszy rozkład, podbija te niepewności, co jest lepszym targetem do uczenia mniejszej sieci.
Trening mniejszej sieci odbywa się z tą samą temperaturą co generowanie soft targetu, podczas predykcji mniejszej sieci temperatura ustawiana jest na 1.
## Dobór odpowiedniego T
![[Pasted image 20260221133112.png]]
Opisane tutaj operacje mówią, że wybór wysokiego T sprawia, że zadanie sprowadza się do minimalizacji MSE co niekoniecznie jest naszym celem. Mówi to też, o konieczności stosowania mnożnika $\frac{1}{T^2}$ w ogólnej funkcji straty, aby zneutralizować wpływ temperatury na siłę aktualizacji wag.
## Funkcja straty
Jako że praca opisuje zadanie klasyfikacji, funkcją straty jest cross entropy loss. A konkretnie średnia ważona z dwóch CEL przy ustawieniu temperatury gdzie T jest równe T które produkuje soft target i ustawieniu $T=1$ które po prostu bada zdolności do klasyfikacji modelu.
W pracy nie jest podana konkretna funkcja straty, ale opis pozwala już dość dobrze odtworzyć. Ma ona kształt:
$$L=\alpha T^2H(P^T,Q^t)+(1-\alpha)H(y,Q^{T=1})$$
Pierwszy czynnik odpowiada za destylację wiedzy, drugi za etykiety. Czynnik etykiet powinien być znacznie mniejszy niż ten destylacji. Do porównania rozkładów wykorzystano entropię krzyżową po wszystkich klasach a nie np Dywergencję KL ze względu na to, że wagi nauczyciela są zamrożone więc $D_{KL}$ zbiega do entropi krzyżowej.
# Eksperyment
W pracy wykonano ciekawy eksperyment w którym w danych treningowych (zazwyczaj są to te same dane co do trenowania nauczyciela) nie znajdowały się cyfry 3. Jako, że wagi sieci nauczyciela były zamrożone nie wpływało to już na niego. Miało to sprawdzić, czy model jest w stanie faktycznie nauczyć się tego co nauczyciel widzi w rozkładach. Otrzymane wyniki wskazywały, że model radzi sobie dużo lepiej z rozpoznawaniem 3 niż model których nie uczył się od nauczyciela. Głównym problemem który prowadził do nie rozpoznawania 3 było to, ze model w ogóle nie zakładał, że coś takiego jak 3 może się pojawić. Więc i bias dla neuronu odpowiedzialnego za 3 był bardzo niski. Naukowcy Eksperymentalnie dobrali bias na poziomie 3.5 aby wzmocnić ten sygnał. Poprawiło to znacznie wyniki detekcji 3, jednocześnie nie pogarszając ich dla innych liczb.
# Wyniki
Sieć uczona od nauczyciela uzyskała dużo lepsze rezultaty od identycznej sieci, która jednak uczyła się w klasyczny sposób i nie odbiegały znacznie od wyników większej sieci.

# Specjaliści
W pracy przedstawione jest jak destylacja może być przydatna do wykorzystania w sieciach wykorzystujących specjalistów. Główną zaletą specjalistów jest możliwość współbierznego trenowania wielu sieci na raz (co jest problematyczne w przypadku MOE). Autorzy zauważają też duże ryzyko **przeuczenia** oraz podają jak można temu zapobiec używając soft targets.


#Destylacja #MOE #Y2015