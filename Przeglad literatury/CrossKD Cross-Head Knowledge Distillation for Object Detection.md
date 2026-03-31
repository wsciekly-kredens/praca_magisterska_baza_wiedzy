https://arxiv.org/pdf/2306.11369
W przypadku klasycznego KD do detekcji obiektów pojawiają się dwa główne problemy: 
- Uczeń skupia się przede wszystkim na naśladowaniu cech nauczyciela, kopiowana jest jego mapa cech, a mniejszą uwagę przykłada się do finalnej predykcji. Problemem jest tu duże zaszumienie cech modelu co przekłada sie na gorsze predykcje
- Uczeń próbuje naśladować predykcje nauczyciela z wykorzystaniem własnej głowy predykcyjnej, co prowadzi do sprzecznych sygnałów, między tym co dostaje od nauczyciela a tym co mówią etykiety zbioru danych.
Podejście opisane w pracy proponuje:
- Podawanie cech wygenerowanych przez ucznia na głowę predykcyjną nauczyciela
- Nauczyciel może zobaczyć jak uczeń postrzega świat i w oparciu o to skorygować wyniki.
- Uczeń otrzymuje czysty sygnał jak optymalizować swoje cechy, żeby były użyteczne dla klasyfikatora wysokiej klasy, nie będąc ograniczonym przez własną głowę predykcyjną.
# Trening
![[Pasted image 20260322131627.png]]
Backbone ucznia jest trenowany przez propagację wstecz z głowy nauczyciela (zamrożone wagi), przez co uczy on się generować cechy zrozumiałe dla ucznia.
Głowa ucznia trenowana jest na etykietach obrazów. Podczas propagacji wstecz zarówno wagi głowy jak i backbone są aktualizowane.
Prowadzi to do sytuacji kiedy w jednym batchu treningowym wagi backbone studenta są aktualizowane zarówno przez backward z głowy nauczyciela jak i ucznia.
# Wyniki
Tak trenowany model osiąga wynik które zdecydowanie przebijają bardziej skomplikowane metody.

#Destylacja #Detekcja_obiektów #Y2024 