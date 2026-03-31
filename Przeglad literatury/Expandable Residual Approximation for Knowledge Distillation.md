https://arxiv.org/pdf/2508.16050
Praca oparta jest na teori Stone'a - Weierstrass'a która mówi, że każda funkcja ciągła w przestrzeni kompaktowej może być aproksymowana z arbitralną precyzją z wykorzystaniem wielomianów lub innych rodzin funkcji spełniających pewne własności algebraiczne i dotyczące separacji.
Metoda ta insiprując się tym podejściem stara się aproksymować model nauczyciela iteracyjnie wykorzystując pomocnicze funkcje których parametry zostały dobrane przez głebokie sieci neuronowe (MBRNet). Gałęzie MBRNet podpięte są do ucznia i trenowane równolegle w procesie destylacji. Sam MBRNet to kilka gałęzi konwolucyjnych dołaczonych do ucznia. Sieć ta pozwala na redukcję luki pojęciowej (braku objętości ucznia względem nauczyciela) i lepszą aproksymację nauczyciela.
# Trening
Podczas treningu trenujemy zarówno ucznia jak i dodatkową sieć. Trening odbywa się na logitach.
Samo zadanie dodatkowej sieci polega na aproksymacji wiedzy rezydualnej, tej której uczeń nie był w stanie reprezentować. Jej struktura jest zmienna. Dla próbki:
1. Uczeń aproksymuje nauczyciela
2. Wyliczana jest różnica ich reprezentacji 
3. Pierwsza gałąź MBRNet bierze tą różnicę i stara się ją aproksymować
4. Liczona jest różnica w odpowiedziach (logitach) nauczyciela i sumy ucznia i pierwszej gałęzi
5. Jeżeli dalej jest za duża to kolejna gałaź bierze różnice i stara się ją aproksymować
6. Proces powtarzamy dla wcześniej predefiniowanej liczby gałęzi
Po tym treningu nasz uczeń może być w trzech trybach:
- S-mode: MBRNet jest całkowicie odcinany i zostaje tylko uczeń
- T-mode: MBRNet zostaje z uczniem. Działa on razem z uczniem przy generowaniu odpowiedzi
- ST-mode: Łączy wyniki wygenerowane przez ucznia z tymi wygenerowanymi przez MBRNet
Główną zaletą MBRNet dla trybu jest wiedza propagowana wstecz podczas uczenia.
Wykorzystaną funkcją straty jest Dywergencja KL.
## Teacher Weight Integration
Dodatkowy moduł (ostatnia warstwa gałezi MBRNet), to skopiowana głowa klasyfikatora. Zastosowanie go wymusza na MBRNet wygenerowanie takiej reprezentacji cech przedostatniej warstwy, która po wejściu do skopiowanej głowy nauczyciela, wypluła logity wyrównujące brakujące różnice punktowe. Zapewnia to też wejścia o bardzo konkretnym kształcie, przez co też stabilność.
# Wyniki
Metoda ta osiąga **SoTA na największych zbiorach danych**. Autorzy porównali tą metodę do:
- Klaszycznego KD
- Metod opartych na cechach
- Nowoczesnych metod logitowych
Metoda ta poradziła sobie lepiej o średnio 1-2 pp od wymienionych metod.
Co ciekawe tryby nie różnią się od siebie znacząco jak chodzi o efekty, wszystkie pokonują konkurentów i tylko wraz ze wzrostem ich złożoności delikatnie poprawiają wyniki.
![[Pasted image 20260311200819.png]]

#Destylacja #Reszty #MBRNet #Y2025