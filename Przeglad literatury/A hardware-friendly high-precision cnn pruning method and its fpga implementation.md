https://www.mdpi.com/1424-8220/23/2/824
Praca porusza problem implementowania sieci splotowych na urządzeniach brzegowych. Wynika to z dwóch problemów: za duży rozmiar, ogromna liczba operacji matematycznych które należy wykonać.
Autorzy podkreślają ze tradycyjne metody są albo bardzo skuteczne ale trudne do przyśpieszenia sprzętowego, albo łatwe dla sprzętu ale drastycznie obniżają dokładność modelu.
Praca opisuje 3 innowacje które mają pomóc z tymi ograniczeniami:
- **Metoda KRP** (Kernel Row-scale regular Pruning): Proponuje usuwanie całych wierszy wewnątrz filtrów splotowych. Dzięki temu zachowamy regularną strukturę danych (dobre dla sprzętu) ale przy tym zachowamy większą elastyczność, niż przy usuwaniu całych filtrów (co poprawi celność)
- **Retraining oparty na "LR Tracking"** (Learning Rate Tracking): Autorzy odkryli, że tradycyjne dotrenowywanie przyciętej sieci ze stałym współczynnikiem uczenia jest mało efektywne. Ich metoda dostosowuje tempo uczenia podczas dotrenowywania w oparciu o dynamikę oryginalnego procesu treningowego, co pozwala szybciej odzyskać celność modelu.
- **Implementacja sprzętowa na FPGA:** Zaprojektowali dedykowany moduł obliczeniowy, który potrafi "pominąć" zerowe wartości (wynikające z przycięcia) bez konieczności stosowania skomplikowanego indeksowania, co zazwyczaj jest wąskim gardłem w architekturach FPGA.
# Wyniki
Testy przeprowadzono na architektach: VGG-16, ResNet-56 i ResNet-110 przy użyciu zbioru CIFAR-10
Połączenie KPR z kwantyzacją pozwoliło na 27 krotne zmniejszenie rozmiaru modelu przy zachowaniu niemal identycznej celności.
Zużycie zasobów spadło o ponad połowę na układach FPGA
![[Pasted image 20260330185459.png]]


#Pruning #Y2023