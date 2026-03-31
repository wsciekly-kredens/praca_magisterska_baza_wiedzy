https://arxiv.org/pdf/2503.16709
Praca dotyczy kompresji modeli w zadaniu detekcji głębi na pojedynczym obrazie. Obromne fundtaion models dobrze radzą sobie z tym zadaniem, jednak wymagają one dużych zasobów sprzętowych.
Zaproponowany przez autorów framework skupia się na kwantyzacji po treningu. 
W tym rozwiązaniu kwantyzacja jest prowadzona do rekordowego poziomu 4 bitów (INT4).
Autorzy zauważyli, że aktywacje w modelach głębi mają specyficzny rozkład. Wprowadzili algorytmy "wygładzania" i kompresji błędów przed i po kwantyzacji aktywacji, co drastycznie redukuje szum w wynikowym obrazie. Zastosowano również metodę rekonstrukcji wag, która minimalizuje błąd rekonstrukcji danych wyjściowych po przejściu przez kwantyzowane warstwy. Autorzy zaprojektowali dodatkowo dedykowany elastyczny akcelerator sprzętowy.
# Wyniki
Tak skompresowane modele pozwalają na osiagnięcie czasu rzeczywistego w estymacji głębi na urządzeniach edge.


#Kwantyzacja #Post_Kwantyzacja #Y2025