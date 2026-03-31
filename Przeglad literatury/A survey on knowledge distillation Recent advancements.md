https://www.sciencedirect.com/science/article/pii/S2666827024000811
Praca jest przeglądem metod destylacji wiedzy.
# Typy destylacji
## Response-based
Klasyczne podejście destylacja w oparciu o logity (soft targets) wytrenowanego modelu
## Feature-based
Destylacja z poszczególnych warstw. Porównywanie warstw modelu z wykorzystaniem specjalnej funkcji aby dostosować warswty ucznia do nauczyciela
## Relation-based
W oparciu o batche danych. Uczeń uczy się mapować zależności między danymi podobnie do nauczyciela
# Podejścia do destylacji
## Offline
Destylacja z wytrenowanego modelu
## Online
Jednoczesne trenowanie nauczyciela i ucznia i destylacja na bierząco (uwspólnianie wiedzy między nimi, może poprawić oba modela)
## Self-distillation
Destylacja z najdalszych warstw sieci do tych wcześniejszych. Pozwala na early stopping, co jest głównym uzyskiem, czyli np dlasyfikację już po 3 a nie po 10 wartwach. 
# Zaawansowane metody
## Oparte o złożone relacje i uwzględniające kontekst
### Cross-Modal Distillation
Polega na transferze wiedzy z nauczyciela wytrenowanego na jednej modalności do modelu operującego na innej np transfer z modelu operującego na obrazach do modelu operującego na dźwieku.
### Graph-Based Distillation
Dla danych o strukturze grafu. Architektura pozwalająca zachować zależności wyższego rzędu i struktury topologicznej sieci.
### Attention-Based Distillation
Zamiast ręcznie dobierać cechy, metoda wykorzystuje mechanizm uwagi, by student automatycznie uczył się skupiać na samych regionach danych co nuaczyciel.
## Metody bez danych i wykorzystujące dane syntetyczne
### Data-Free Distillation
Pozwala na destylacje bez dostępu do oryginalnych danych treningowych modelu nauczyciela.
[[What Makes a Good Dataset for Knowledge Distillation]]
### Adversarial Distillation
Łączy KD z treningiem jak w GAN. Student nie tylko uczy się naśladować nauczyciela ale też oszukiwać dyskryminator, co pozwala na wytrenowanie bardziej odpornego na ataki modelu.
## Kompresja modelu i optymalizacja architektury
### Quantized Distillation
Łączy zmniejszanie precyzji wag sieci z destylacją wiedzy. Nauczyciel jest pełnej precyzji, a destylacja następuje do skwantowanego ucznia.
[[QKD Quantization-aware Knowledge Distillation]]
### NAS-Based Distillation
Wykorzystuje Neural Architecture Search do znalezienia optymalnej architektury dla modelu ucznia. Balansuje pomiędzy wysoką wydajnością a zminimalizowaniem rozmiaru modelu podczas destylacji.
## Metody destylacji zespołowej
### Lifelong Distillation
Przeciwdziała katastroficznemu zapominaniu podczas uczenia. Nauczyciel pomaga zachować wiedzę, podczas trenowania ucznia.
### Mult-teacher Distillation
Jeden model uczeń czerpie wiedzę z wielu modelu nauczycieli.

#Destylacja #Y2024