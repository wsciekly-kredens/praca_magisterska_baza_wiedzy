https://arxiv.org/pdf/2408.07703
Klasyczna destylacja wiedzy, w której wykorzystuje się logity, ma jedna wade, uczeń za wszelką cenę stara się naśladować logity nauczyciela, nawet jak są błędne. Wcześniejsze próby wzbogacania ich o GT (typowe podejście przy uczeniu modeli) psuje ten rozkład i prowadzi do mniej wydajnej destylacji. Praca ta stara się zaadrasować ten problem.
Proponowana metoda została nazwana Refined Logit Distillation. Polega ona na wykorzystaniu faktycznych etykiet do udoskonalania logitów nauczyciela. Pozwala to na uodpornienie procesu uczenia na błędne klasyfikacje nauczyciela, jednocześnie zachowując relację między klasami.
Rozwiązanie to opiera się na składowych:
1. Sample Confidence Distillation - destylowanie wiedzy z uwzględnieniem pewności modelu co do danych próbek
2. Masked Correlation Distillation - stosowanie specjalnych masek po to, aby mimo korekcji błędów zachować "miękkie" relacje między klasami.
Sam proces polega na przekazaniu od ucznia wartości pewności jaką nauczyciel przypisał prawdziwej klasie, uczy się wtedy on niskiego zaufania, ale ignorowana jest błędna główna predykcja nauczyciela co nie wpływa na jakość ucznia. Przekazanie całej wiedzy logitowej odbywa się dzięki maskowaniu. Algorytm całkowicie maskuje informacje o klasie poprawnej oraz te najbardziej zaburzone przez błąd. Zmusza to ucznia od naśladowania relacji między pozostałymi klasami.
# Wyniki
![[Pasted image 20260324143857.png]]


#Destylacja 