https://arxiv.org/pdf/2402.03119
W tradycyjnym KD uczeń stara się naśladować tylko wyniki nauczyciel (logity). Jak uczy logika, poprawne wnioski można uzyskać z błędnych przesłanek, w przypadku KD również istnieje takie zagrożenie. Podejście opisane w tej pracy proponuje, aby uczeń nie kopiował tylko wyników ale i przemyślenia nauczyciela. 
Przemyślenia te to zazwyczaj mapy istotności, które wskazują na to, które cechy wejściowe były najważniejsze w podjęciu decyzji.
Osiąga się to dodając do standardowej funkcji straty komponent króry minimalizuje różnicę między mapą wyjaśnień ucznia i nauczyciela.
Metoda ta jest model agnostic i nie wymaga dodatkowych parametrów w fazie wnioskowania. 
Ta metoda szkolenia przekłada się na lepsze wyniki od sieci szkolonych stricte na logitach.

#Destylacja #Y2024