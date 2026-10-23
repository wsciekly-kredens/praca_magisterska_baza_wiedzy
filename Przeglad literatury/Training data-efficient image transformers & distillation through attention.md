https://arxiv.org/pdf/2012.12877

Praca proponuje model DeIT. Jest to model transformerowy. Z architektonicznego punktu widzenia jest praktycznie identyczny co ViT. Kluczem tej pracy jest pokazanie, że problemem Transformerów nie jest przetwarzanie obrazów a sposób ich treningu. Co od zasady ViT potrzebowały ogromnych zbiorów danych treningowych żeby uzyskiwać możliwość generalizacji. Różni się trening. Używa się bardzo mocnej augmentacji danych i regularyzacji.

Taki reżim treningowy pozwala na efektywny trening dużo mniejszych sieci.

Dodatkowo praca opisuje sposób destylacji z transformera wykrzystujący token destylacji na wejściu.

# Wykorzystane techniki augmentacji
## Mixup
Nakładanie na siebie dwóch różnych zdjęć i wymaganie przewidzenia obu etykiet jednocześnie
## CutMix
Wycinanie fragmentów jednego zdjęcia i wklejanie go w inne
## RandAugment
Losowe, silne zniekształcenia kolorów, kontrastu, obrotu, filtra
## Rand Erasing
Losowe zakrywanie prostokątnych fragmentów obrazu czarnymi plamami, by model nie polegał tylko na jednej najbardziej oczywistej cesze obiektu
# Regularyzacja sieci
## Stochastic Depth
Losowe wyłączenie całych warstw transformera w trakcie treningu co wymusza, by każda warstwa uczyła się przydatnych cech i nie polegało ślepo na innych
## Label smoothing
Zamiast wymagać 100% pewności od modelu uczono go pewności na poziomie 90% dla dominującej klasy.


#ViT #Y2020 