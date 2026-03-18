https://arxiv.org/pdf/1911.12491
Praca opisuje metodę połączenia destylacji wiedzy z kwantyzacją.
Proste połączenie tych metod może prowadzić do niezadowalających wyników, dlatego konieczne jest opracowanie lepszych sposobów realizacji tego. Zastosowanie tego wprost jeszcze bardziej potęguje kluczowy problem destylacji: model ucznia nie ma wystarczającej pojemności do dokładnego odtworzenia nauczyciela, a kwantyzacja dodatkowo zmniejsza wymiar jego wag.
# Trening
Generalnie praca zakłada podejście : Kwantyzacja -> Destylacja
Aby zaradzić problemowi pogorszenia jakości modelu destylowanego po kwantyzacji, praca proponuje 3 fazowy trening:
1. **Faza self studying**: Na początku uczeń jest pozostawiony sam sobie- ignoruje nauczyciela. Skwantowana sieć jest standardowo douczana na danych treningowych. Ta faza działa niejako jako inicjalizator wag.
2. **Faza co-studying**: Kluczowy wkład w tej pracy. Obie sieci wchodzą w interakcję, ale wagi nauczyciela **nie są zamrożone** i nauczyciel nie jest bezwzględny. Nauczyciel trenuje się na podstawie tego z czym radzi sobie (lub nie) uczeń. Dzięki temu nauczyciel staje się przyjazny kwantyzacji: generuje wyjścia, które są znacznie łatwiejsze dla przyswojenia przez sieć o niskiej precyzji. Ta faza oparta jest na destylacji wiedzy online. Oba modele są trenowane.
3. **Faza tutoringu**: Tutaj następuje właściwa destylacja. Nauczyciel przekazuje swoją wiedzę do ucznia już w klasycznym paradygmacie (ofline, z zamrożonymi wagami).
# Wyniki 
Model osiągnął wyniki SoTA dla ImageNet i CIFAR. Metodę porównano do wiodących metod (w tym czasie) kwantyzacji. Porównano je na dla różnych poziomow kwantyzacji (W4A4 - wagi i aktywacje zredukowane do 4 bitów, W3A3 - wagi i aktywacje zredukowane do 3 bitów, ...)
![[Pasted image 20260314161111.png|697]]
![[Pasted image 20260314161430.png]]

#Kwantyzacja #Destylacja #Pre_Kwantyzacja