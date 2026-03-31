https://arxiv.org/pdf/2507.15911
Praca proponuje zmienione podejście do funkcji straty. Standardowy softmax zaciera drobnoziarniste lokalne relacje między klasami. Aby rozwiązać ten problem autorzy proponują podejście LDRLD (Local Dense Relational Logit Distillation). 
Jej głównymi filarami są:
- **Rekurencyjne rozprzęganie i łączenie logitów (Recursive decoupling and recombining):** Zamiast polegać na jednym, globalnym rozkładzie klas, LDRLD "rozbija" (decouples) logity, aby model mógł analizować bezpośrednie, lokalne relacje między poszczególnymi parami kategorii. Dzięki temu uczeń otrzymuje znacznie dokładniejszy sygnał edukacyjny, pomagający mu precyzyjniej wyznaczać granice decyzyjne między podobnymi do siebie obiektami.
    
- **Strategia Adaptive Decay Weight (ADW):** Zauważono, że nie wszystkie relacje między klasami mają równe znaczenie (relacja "kot vs. pies" może być dla modelu trudniejsza niż "kot vs. samochód"). Wprowadzono dynamiczny mechanizm wag:
    
    - **IRW (Inverse Rank Weighting):** Przypisuje większe wagi parom kategorii, które znajdują się blisko siebie w rankingu prawdopodobieństw. Im trudniejsze klasy do rozróżnienia, tym większą wagę model przykłada do ich relacji.
        
    - **ERD (Exponential Rank Decay):** Kontroluje wykładniczy zanik tych wag w oparciu o ich sumaryczne wyniki rankingowe, co stabilizuje proces uczenia.
        
- **Kompletność wiedzy (Non-target knowledge):** Po zastosowaniu powyższych kroków, metoda dokonuje dodatkowej destylacji informacji o pozostałych klasach (innych niż docelowa). Zapewnia to, że żadna pożyteczna informacja od nauczyciela nie zostaje utracona.
# Wyniki
![[Pasted image 20260331175902.png]]

#Destylacja #Y2026