# Worth the note
- Structured pruning w zastosowaniu w CNN
- Pruning before training bo pozwala zaoszczędzić już na treningu
# Structured pruning
Zamiast usuwać pojedyncze wagi usuwa całe struktury: kanały, filtry (cnn), czy neurony. Dzięki temu nie prowadzi do macierzy rzadkich. Macierze stają się mniejsze przez co operacje na nich są szybsze.
# Pruning before learnig
Różne podejścia np One-shot - na losowa zainicjowanej sieci przepuszcamy dane i badamy aktywację poszczególnych neuronów, wywalamy te najsłabiej.
Maksymalnie kilka epok przed obcięciem.
# Hipoteza Loteryjnego Losu
Każda duża podsieć ma mniejszą podsieć, która pozwala na uzyskanie praktycznie takich samych wyników, tą mniejszą sieć nazywany zwycięskim biletem.

#Pruning #Hipotza_Loteryjnego_Losu