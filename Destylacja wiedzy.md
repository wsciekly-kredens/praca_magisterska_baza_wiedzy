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