https://arxiv.org/pdf/2402.00084
Praca ta opisuje podejście do kompresji modelu który pozwala na przycinanie wag modelu jeszcze przed samym głównym treningiem i pozostawienie tylko tych wag, które są podatne na destylacje.
Opisany framework jest dwuetapowy, a jego główną koncepcją jest poszukiwanie wag podatnych na destylację.
# Wybór wag
Wagi nie są oceniane pod kątem tradycyjnego zadania (np. klasyfikacji z funkcją straty cross-entropy), EPSD modyfikuje kryterium oceny.
1. Algorytm analizuje jak każda waga wpłynie na mechanizm samodestylacji
2. Wagi najbardziej podatne na samodestylację, to takie które mają największy wkład w płynny transfer wiedzy wewnątrz modelu.
Wybór wag do przycięcia odbywa sie z wykorzystaniem metryki ważności która uwzględnia charakterystykę samodestylacji.
- Przez sieć przepuszczana jest partia danych
- Zamiast liczyć błąd klasyfikacji sieć oblicza, jak dobrze jej wewnętrzne, płytkie warstwy naśladują najgłębszą warswę
- Następuje propagacja gradientu wstecz
- Dla każdej wagi obliczana jest wartość zmodyfikowanej funkcji celu, następnie wagi są sortowane.
- Wagi z najniższym wynikiem są odrzucane, a wagi z najwyższym zostają zachowane na trening.
# Samodestylacja
Powstała rzadka sieć neuronowa jest poddawana właściwemu treningowi. Dzięki pruningowi ten proces jest znacznie szybszy.
Sama samodestylacja polega na tym, że sieć uczy się naśladować samą siebie. Proces polega na fizycznej modyfikacji sieci podczas treningu. W samodestylacji do wcześniejszych warstw są doczepiane dodatkowe klasyfikatory pomocnicze. W tym układzie ostateczny klasyfikator pełni rolę nauczyciela dla wcześniejszych warstw sieci. Podobnie jak w klasycznej destylacji tutaj również uczeń (wcześniejsze warstwy) uczy się na miękkich targetach sieci. 
## Liczenie błędu sieci
Całkowity minimalizowany błąd jest sumą dwóch elementów.
1. Straty klasyfikatora (Cross-Entropy) - jak bardzo model się myli
2. Strata destylacji (KLD) - Jak bardzo prognozy klasyfikatorów pomocniczych (Uczniów) różnią się od prognoz głównego klasyfikatora
Chociaż proces samodestylacji nie zmienia fizycznego rozmiaru modelu, to poprawia jego rezultaty.
Największymi zaletami tego podejścia są: Regularyzacja i zapobieganie przeuczeniu, brak zanikania gradientu, możliwość "early exit" kiedy pewność na wcześniejszych warstwach jest duża.
# Wyniki
![[Pasted image 20260322140402.png]]
![[Pasted image 20260322140528.png]]



#Destylacja #Y2024