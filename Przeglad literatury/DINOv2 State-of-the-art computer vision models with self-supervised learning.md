https://arxiv.org/pdf/2304.07193
Ta notatka to tylko brakedown destylacji wiedzy użytej dla tego modelu.
# Standardowa destylacja
Do uzyskania mniejszych wersji modelu wykorzystano destylację danych. Destylowano Wizyjny Transformer. Kluczową zmianą względem klasycznej destylacji wiedzy jest wykorzystanie EMA, czyli wykładniczej średniej kroczącej wag modelu. Dla każdej porcji danych wagi modelu ucznia mogą się dynamicznie zmieniać. Z tego powodu zastosowano dodatkowy model, który uśrednia te wagi licząc wykładniczą średnią kroczącą. To właśnie ten dodatkowy model jest finalną wersją.
# Samodestylacja
W tej pracy samodestylacja została wykorzystana jako mechanizm pretreningu właściwego ogromnego modelu. Sam mechanizm wygląda następująco:
Podczas pretrenignu inicjowane są dwie identyczne ogromne sieci. Z czego jedna jest nauczycielem a druga uczniem.
- Wagi ucznia są aktualizowane klasyczni, poprzez propagację wsteczną na podstawie funkcji straty
- Wagi nauczyciela są aktualizowane z wykorzystaniem EMA z wag ucznia.
## Strategia multi-crop
Jako że DINOv2 to self-supervised model to model musi rozumieć obraz bez etykiet. Ma to swoje odwzorowanie w treningu. Aby to osiągnąć manipulujemy danymi wejściowymi:
- Globalne wycinki, to duże fragmenty obejmujące większość obrazu w dużej rozdzielczości.
- Lokalne wycinki, to małe fragmenty, często będące detalami obrazu
Co do zasady nauczyciel widzi tylko wycinki globalne, a uczeń widzi wszystkie wycinki.
Tutaj też dochodzimy do celu treningu. Uczeń ma przetworzyć lokalny wycinek i wygenerować taką taką samą reprezentację jak nauczyciel patrzący na duży wycinek.


#Destylacja #ViT 