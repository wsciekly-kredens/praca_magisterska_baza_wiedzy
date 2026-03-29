https://arxiv.org/pdf/2502.16638
Autorzy tej pracy zauważyli, że pruning i kwantyzacja wpływają na siebie nawzajem. Stosowanie ich osobno nie pozwala na pełne wykorzystanie ich potencjału i osiągnięcie optymalnego tradeoffu między rozmiarem a dokładnością.
Proponują framework GETA. Jego kluczowe cechy to:
- QADG: Automatyczna analiza grafu zależności modelu, która pozwala zidentyfikować, które części sieci można przyciąć i kwantyzować bez naruszania spójności architektury. 
- Optymalizator QASSO: nowy algorytm który rozwiązuje zarówno problem rzadkości (sparsity) i kwantyzacji. Pozwala na naukę optymalnej szerokości bitowej dla każdej warstwy (mixed-precision) przy zachowaniu ograniczeń strukturalnych.
- Zintegrowana strategia uczenia: GETA wprowadza mechanizmy, które pozwalają modelowi decydować w trakcie treningu, czy lepiej jest usunąć dany parametr, czy reprezentować go z mniejszą precyzją.
Kluczową cechą podejścia jest to że jest agnostyczny względem frameworku. 
# Wyniki
Metoda osiąga wyniki lepsze od konkurencyjnych metod. Osiąga mniejsze modele, które mają wyższą dokładność, a proces treningu jest automatyczny.


#Pruning #Kwantyzacja 