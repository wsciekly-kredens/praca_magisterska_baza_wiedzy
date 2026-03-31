https://arxiv.org/pdf/2502.08606
Praca wprowadza prawo skalowania dla problemu destylacji wiedzy. Jej celem jest odpowiedź na pytanie: Jeżeli mamy określony budżet obliczeniowy, jak optymalnie rozdzielić go między trening nauczyciela i ucznia, aby uzyskać jak najlepszego ucznia?
# Wzór
Autorzy opracowali wzór, który pozwala na przewidzenie cross-entropy dla ucznia na podstawie dostępnych zasobów. Jest on skuteczny dla wcześniej nie widzianych kombinacji wielkości ucznia i nauczyciela.
# Wpływ nauczyciela
Rozmiar modelu nauczyciela oraz ilość danych (tokenów) użytych do jego treningu wpływają na wydajność ucznia **wyłącznie poprzez końcową jakość (cross-entropy) samego nauczyciela**. Oznacza to, że dla ucznia nie ma znaczenia, czy nauczyciel jest mały, ale trenowany na ogromnej ilości danych, czy duży, ale trenowany krócej – liczy się tylko jego ostateczna zdolność predykcyjna.
# Capacity Gap
Jest to zjawisko w którym zbyt dobry nauczyciel pogarsza ucznia ([[Knowledge Distillation from A Stronger Teacher]]). Praca ta wyjaśnia, że wpływ straty nauczyciela na stratę ucznia opiera się na funkcji potęgowej, która zmienia swoje zachowanie w zależności od względnej pojemności uczenia się obu modeli (ich przestrzeni hipotez i zdolności optymalizacyjnych). 
# Destylacja kontra nauka od zera
Destylować kiedy mamy już wytrenowany model bazowy, lub destylujemy do wielu uczniów.
Destylacja może nie być najlepsza kiedy wymagane by było wytrenowanie nauczyciela od zera (nie od poziomu modelu bazowego), tylko po to żeby destylować jednego ucznia. W takiej sytuacji lepiej wytrenować ucznia.
Co ważne przy odpowiednio dużym budżecie obliczeniowym tradycyjne uczenie nadzorowane finalnie zawsze zrówna sie z optymalną destylacją lub nawet ją przewyższy.


#Destylacja #Y2025 