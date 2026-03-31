https://proceedings.neurips.cc/paper_files/paper/2024/file/78526d7ad4a2532bd91416e948b9644c-Paper-Conference.pdf
Praca próbuje pokazać, że dywergencja KL nie jest najlepszą metryką podczas destylacji wiedzy. Argumentują to tym, że porównuje ona jedynie prawdopodobieństwo konkretnej klasy miedzy nauczycielem a uczniem, bez mechanizmu porównywania między klasami (np lew jest bardziej podobny do tygrysa niż słonia, KL tego nie uwzględnia). Dodatkowo ciężko to zaaplikować do pośrednich warstw sieci, ponieważ nie uwzględnia geometrii przestrzeni w której cechy w pośrednich warstwach są przetwarzane.
Praca proponuje techniki oparte na odległości Wessersteina.
Metoda ta jest dobra zarówno dla architektur jednorodnych (np. ResNet do ResNet), jak i niejednorodnych (np. Transformer do CNN).
# WKD-L
Służy do destylacji na poziomie wyjścia modelu. Wykorzystuje dyskretną odległość Wessersteina, aby umożliwić porównanie między różnymi kategoriami. Autorzy stosują metodę CKA (central Kernel Alignment) aby zmierzyć podobieństwo między klasami na podstawie cech wyekstrahowanych przez nauczyciela, co pozwala na wybranie podobnych do siebie kategorii.
# WKD-F
Metoda służy do destylacji z pośrednich warstw sieci, ale tego nie planuje używać w magisterum.
# Wyniki
WKD-L przewyższa silne warianty oparte na KLD.
![[Pasted image 20260323200445.png]]


#Destylacja #Y2024