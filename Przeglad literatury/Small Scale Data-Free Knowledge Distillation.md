https://arxiv.org/pdf/2406.07876
Podejście data-free jest wykorzystywane kiedy oryginalne dane treningowe nie są dostępne. Tradycyjnie uczy się modele generatywne, które w oparciu o wiedzę wyciągniętą z sieci nauczyciela wytworzyć zbiór sztucznych danych. Jest to jednak wolne i wymaga wiele zasobów.
Autorzy pracy podważają podejście w myśl którego potrzeba ogromu danych do udanej destylacji. Pokazują, że jest to możliwe nawet dla małego zbioru danych, pod warunkiem, że jego jakość i  rozkład będzie wysoce zoptymalizowane.
Proponują podejście które nazywają SSD-KD, które opiera się na dwóch filarach:
1. Funkcja modulująca: precyzyjnie balansuje rozkład generowanych klas. Pilnuje aby wytworzone dane były różnorodne.
2. Prioretytzująca funkcja próbkująca: Odpowiada za dobór optymalnych próbek do nauki na danym etapie.
# Wyniki
![[Pasted image 20260324155030.png]]


#Destylacja #Data-Free #Y2024