https://ieeexplore.ieee.org/document/10465265
Praca stara się zaadresować problemy capacity gap oraz jednokierunkowaości podejścia offline.
Jako rozwiązanie proponują metodę FFKD, inspirowaną ludzkim sposobem pozyskiwania wiedzy (nauczanie i egzaminowanie).
Metoda składa się z dwóch etapów:
A. Forward Knowledge Distillation (Nauczanie)
To proces offline, w którym nauczyciel przekazuje wiedzę uczniowi. Nowością jest zastosowanie mechanizmu **CKA (Centered Kernel Alignment)** do ważenia kanałów.
- **Cel:** Uczeń uczy się map cech i „miękkich etykiet” od nauczyciela.
- **Rola CKA:** Mierzy podobieństwo reprezentacji między nauczycielem a uczniem. Jeśli uczeń dobrze „rozumie” dany kanał (wysoki wynik CKA), waga destylacji jest odpowiednio dostosowywana, aby transfer był bardziej precyzyjny.
B. Feedback Knowledge Distillation (Egzaminowanie)
To proces online, w którym role się odwracają: nauczyciel otrzymuje informację zwrotną od ucznia.
- **Cel:** Nauczyciel optymalizuje swoją strategię nauczania, dostosowując parametry do możliwości ucznia.
- **Mechanizm zwrotny:** Jeśli uczeń słabo radzi sobie z danymi blokami informacji (niski wynik CKA), te fragmenty są „zgłaszane” nauczycielowi do poprawy strategii.
# Wyniki
Metoda osiąga bardzo dobre wyniki na popularnych zbiorach danych. W niektórych architektach uczeń osiąga lepsze wyniki od nauczyciela. Sam nauczyciel również staje się lepszy.


#Destylacja #Y2024 