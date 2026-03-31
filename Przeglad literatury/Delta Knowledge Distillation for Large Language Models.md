https://arxiv.org/pdf/2509.14526
Praca opisuje metodę destylacji w której głównym założeniem jest nie przekazywanie rozkładu odpowiedzi modelu jak w standardowej destylacji a uczenie modelu tak aby model ucznia zmieniał się tak samo podczas fine tuningu jak model nauczyciela.
# Trening
Do treningu wykorzystano dwa modele bazowe. Jeden duży 72B parametrów jako nauczyciel (rodzina Qwen2). Jako model ucznia wtykorzystano model o 7B (lub 1.5B) parametrów. Jako że to modele bazowe, to były one wcześniej wyuczone i konieczne było jedynie douczenie ich do dziedziny badanego problemu (fine tuning).
Kluczowe dla dla metody opartej o delte jest douczanie. Podczas niego zachodzi pewna zniana w modelu i tą tą zmianę z modelu nauczyciela powinien naśladować model ucznia.
Podczas douczania wykorzystano dwa reżimy:
- **token-level KD**, gdzie model ucznia ma bezpośredni dostęp do wewnętrznych rozkładów prawdopodobieństwa nauczyciela. To w tym etapie wyliczana jest delta którą odtworzyć musi model ucznia
- **Sequence-level KD**, tutaj analizowane jest całe wyjście modelu (cała sekwencja tokenów)
# Eksperymenty
Modele uczniów zostały porównane modelami które były destylowane w bardziej klasyczny sposób. Porównywany ich osiągnięcia względem:
- Klasycznego KD gdzie odtwarzano cały rozkład
- Destylację na poziomie sekwencji, gdzie model uczy się na pełnych odpowiedziach tekstowych wygenerowanych przez nauczyciela.
Do ewaluacji wykorzystano metryki z rodziny ROUGE, które mierzą jak zbieżne są teksty wygenerowane z docelowymi.
# Wyniki
Wyniki modelu trenowanego na delcie są lepsze od innych podejść.
![[Pasted image 20260310170817.png]]


#Destylacja #Y2025