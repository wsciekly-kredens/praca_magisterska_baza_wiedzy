https://arxiv.org/pdf/2411.12817
Praca skupia się na problemie przenoszenia wiedzy z nauczyciela do ucznia. Często model bazowy (nauczyciel) jest trenowany na danych niedostępnych w domenie publicznej. Przez to transfer wiedzy staje się bardziej skomplikowanym zadaniem. Praca poszukuje cech które powinien posiadać dobry zbiór zastępczy (ten który wykorzystamy do przeniesienia wiedzy z nauczyciela do ucznia).
# Obserwacje
- Zbiór danych wykorzystany do transferu wiedzy nie musi być z tej samej domeny co zbiór danych treningowych. Co więcej mogą być to syntetyczne, nierealistyczne dane, a transfer wiedzy i tak może być udany. Rodzi to pytania o to czy wagi w modelu mogą skrywać jakieś szersze prawidłowości i czy modelowana przestrzeń jest ogólna.
- Nawet wykorzystując abstrakcyjne obrazy (w pracy zbiór "Leaves" generujący kształty geometryczne, takie jak koła, kwadraty, trójkąty o jednolitych kolorach, wykorzystano nawet szum) destylacja może być owocna.
- Udało się wyodrębnić uniwersalne kryteria charakteryzujące dobry zbiór do destylacji.
- Badacze opracowali nową metodę bazującą na adversarial attack żeby zoptymalizować transfer weidzy.
# Adversarial attack
Polega na nałożeniu na obraz specjalnego szumu (niezauważalnego dla człowieka) który sprawia, że działanie modelu (predykcje) są zaburzone. Dla zdjęcia kota jest możliwe wyznaczenie takiego szumu i nałożenie go na obraz, aby wytrenowany model ocenił to jako psa.
# Cechy dobrego zbioru treningowego
Badacze doszli do wniosku, że kluczową cechą obrazów w zbiorze zastępczym nie jest to jakiej jakości są obrazy, tylko jak aktywują model nauczyciela. Mając to na uwadze podali oni następujące cechy:
- **Wysoka entropia predykcji**: Obraz po przepuszczeniu przez nauczyciela nie powinien dawać 100% pewności przynależności do danej klasy. Najwięcej wiedzy jest w bogatym rozkładzie (multimodalnym).
- **Zbalansowana reprezentacja klas**: Do dobrego transferu potrzebna jest odpowiednia aktywacja nauczyciela, najlepiej żeby była on równomierna pomiędzy klasami.
- **Różnorodność i złożoność wizualna**: Aby uczeń nauczył się wykrywać potrzebne kształty, krawędzie, tekstury, itp. zbiór zastępczy musi je posiadać. 
# Metoda oparta o adversarial attack
1. Bierzemy dowolny zbiór (suboptymalny).
2. Przepuszczamy go przez nauczyciela.
3. Badamy aktywację nauczyciela na obrazy z tego zbioru.
4. Modyfikujemy obrazy tak aby dawały większą entropię oraz bardziej zbalansowany rozkład prawdopodobieństwa na wyjściu z nauczyciela (czyli był bliżej dobrego zbioru).
5. Tak poprawiony zbiór wykorzystujemy do faktycznej destylacji wiedzy.
# Wyniki
W pracy wykorzystano klasyczne KD. W eksperymentach porównano modele otrzymane przez trening na tym zbiorze do modeli otrzymanych poprzez trening na danych dziedzinowych i poza dziedzinowych.
Eksperymenty pokazały, ze optymalizowanie danych może zbliżyć wyniki do wyników otrzymanych przez model trenowany na danych naturalnych.
![[Pasted image 20260314115202.png]]
#Destylacja #Dane_treningowe