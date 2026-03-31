https://proceedings.neurips.cc/paper_files/paper/2022/file/da669dfd3c36c93905a17ddba01eef06-Paper-Conference.pdf
Autorzy pracy zauważają, że istnieje zjawisko które można określić paradoksem silnego nauczyciela. Wtedy funkcja straty oparta o DKL okazuje się zawodna w destylacji i daje wyniki gorsze niż przy destylacji ze słabszego nauczyciela. Dla zbyt dużych nauczycieli staje się to być bardzo trudne zadanie dla ucznia aby naśladować jego zachowania. Takie wyniki prowadzą do gorszego wyniku niż uczenie od zera.
Jako rozwiązanie proponują metodę **DIST** (Knowledge Distillation from A Stronger Teacher).
# DIST
Zamiast dążyć do idealnego odwzorowania wartości liczbowych, autorzy proponują **relaksację dopasowania**. Kluczem jest zachowanie **relacji** między przewidywaniami, a nie ich bezwzględnych wartości.
Kluczowym założeniem metody jest wykorzystanie korelacji Persona zamiast dywergencji KL.
Metoda ta opiera się na dwóch poziomach.
- Relacji inter-klasowa: Student uczy się korelacji między rozkładami prawdopodobieństwa dla różnych klas w ramach jednej instancji.
- Relacja intra-klasowa: Student uczy się korelacji między przewidywaniami dla różnych instancji w ramach tej samej klasy (np. które zdjęcie kota jest dla nauczyciela bardziej kotem).
# Zalety i czemu to działa
- Korelacja Persona pozwala na elastyczność. Jest niezmienna względem liniowych przekształceń (skalowania i przesuniecia), co pozwala studentowi na zachowanie "hierarchii preferencji", bez konieczności kopiowania jego **specyficznej pewności siebie**.
- Metoda jest uniwersalna zarówno względem problemu jak i architektury
- Jest bardzo prosta w implementacji



#Destylacja #Y2022