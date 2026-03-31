https://arxiv.org/pdf/2403.01427
Praca ta adresuje problem związany z klasycznym KD. Klasyczne KD zakłada porównywanie logitów obu modeli, przy czym zakłada, że nauczyciel i uczeń powinni mieć identyczny zakres i wariancję logitów. Jest to problematyczne założenie bo modele mają różną architekturę i pojemność. Co do zasady nauczyciel generuje logity o dużej rozpiętości a uczeń o mniejszej skali. Prowadzi to do problemów ucznia z dokładnym kopiowaniem logitów nauczyciela. Uczeń powinien kopiować relacje między klasami.
Autorzy jako rozwiązanie proponują standaryzowanie logitów obu modeli z wykorzystaniem Z-score przed obliczeniem funkcji kosztu. W ten sposób otrzymujemy logity o średniej 0 i wariancji 1.
Wielką zaletą tej metody jest to, że jest ona plug and play - nie wymaga modyfikowania modelu i można ją dodać do każdej destylacji opartej o logity.
Kluczowym pytaniem które się pojawia jest "Ale przecież softmax jest znormalizowany, to co daje dodatkowa standaryzacja?". Tutaj dochodzimy do definicji logitu, są to surowe wyjścia z sieci przed softmaxem. Kluczową zaletą tutaj jest możliwość wyeliminowania parametru temperatury, który musiał byc dobierany ręcznie, nie tracą na wynikach.
Sam schemat wygląda w tej pracy następująco:
Logiy->Standaryzacja->Softmax->Funkcja straty
Taka destylacja osiąga zaskakująco dobre wyniki
# Wyniki
W pracy porównano wiele różnych par architektur na zadaniach ImageNet i Cifar-100
![[Pasted image 20260317190644.png]]
![[Pasted image 20260317190807.png]]


#Destylacja #Y2024