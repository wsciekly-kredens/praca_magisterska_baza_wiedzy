https://arxiv.org/pdf/2504.08966
Modele wizyjne przetwarzają masę patchy. Typowe jest, że ich część jest nadmiarowa i nie niesie informacji o obiekcie na obrazie (np fragmenty nieba) lub są mało istotne dla zapytania. Pozbywając się ich możemy znacznie zmniejszyć koszt zapytania. 
Autorzy proponują metodę która identyfikuje niepotrzebne patche bez konieczności wykorzystywania flash attention ( i wyliczania attention scores). Jest to EUTI. Identyfikuje ona patche o niskiej istotności. 
Drugą częścią est klasteryzacja - DBDPC. Zamiast usuwać podobne tokeny, są one łączone jeżeli niosą podobną informację wizualną.
Dodatkowo wykorzystano mechanizm odzyskiwania, który patche uznane za nieistotne ale będące blisko tych istotnych włącza do ich klastrów. Dzięki temu mamy gwarancję nie pominięcia żandych ważnych elemetnów.
Oba te elementy składają się na PACT.
# Wyniki
Takie podejście przekłada się na znaczne przyśpieszenie działania modelu jednocześnie oszczędza pamięć modelu. To wszystko dzieje się bez zauważalnych strat w jakości modelu.


#Pruning #Data_copression