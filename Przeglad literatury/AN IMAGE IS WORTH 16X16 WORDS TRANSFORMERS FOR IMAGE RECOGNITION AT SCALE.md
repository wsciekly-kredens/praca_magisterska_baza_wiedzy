https://arxiv.org/pdf/2010.11929
Praca wprowadza architekturę wizyjnego transformera, próbę przeniesienia architektury do NLP na kanwę obrazów.
W architekturze tej obraz jest traktowany jako sekwencja patchy (tak jak w standardowym transformerze jako sekwencja tokenów), które mają rozmiar 16x16 pikseli i nienakładają się na siebie. Każdy patch jest wypłaszczany do wektora i przepuszczany przez warstwę liniową tworzącą jego embedding. Wykorzystany koder jest bardzo podobny do tego w standardowym transformerze.
Do każdego patcha jest też dodawany embeding pozycyjny, aby model wiedział gdzie na obrazie się dany patch znajduje.
Sama klasyfikacja odbywa się z wykorzystaniem specjalnego wektora \[CLS\]  który agreguje informacje z kolejnych patchy, ponieważ patche przetwarzane są równolegle. To w oparciu o ten wektor podejmowana jest finalna decyzja modelu.
# Wady
Główną wadą tej architektury jest konieczność wykorzystania dużo wiekszego zbioru danych do trenowania, żeby uzyskać sensowne wyniki w porównaniu do CNN. Ta zależność nie jest jednak liniowa to znaczy, że przy dalszym powiększaniu zbioru danych może okazać się, że mając ViT i CNN trenowane na takim samym wielkim zbiorze danych, to ViT da lepsze wyniki.
# Zalety
Jak opisałem pretrenowany model bazowy ViT po transfer learningu często pokonuje douczony model CNN.
![[Pasted image 20260316132213.png]]
#ViT