Temat pracy: "**Metody kompresji modelu uczenia głębokiego**"
# Aktualnie czytane prace
Distilling the Knowledge in a Neural Network: https://arxiv.org/pdf/1503.02531
An Survey of Neural Network Compression: https://arxiv.org/pdf/2006.03669
Knowledge Distillation: A Survey: https://arxiv.org/pdf/2006.05525
Deep Compression: Compressing Deep Neural Networks with Pruning, Trained Quantization and Huffman Coding: https://arxiv.org/pdf/1510.00149
A Survey on Model Compression for Large Language Models: https://arxiv.org/pdf/2308.07633
Quantization and Training of Neural Networks for Efficient Integer-Arithmetic-Only Inference: https://arxiv.org/pdf/1712.05877
MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications: https://arxiv.org/pdf/1704.04861

# Podstawowe metody
## Pruning
Usuwanie mało istotnych wag lub neuronów z sieci, dzięki temu otrzymujemy rzadszą macierz.
## Kwantyzacja (Quantization)
Redukcja precyzji reprezentacji liczbowej wag i aktywacji np z float32 do float8
## Destylacja wiedzy (Knowledge Distilation)
Trenowanie mniejszej sieci tak, aby naśladowała działanie większej sieci. (Fajne podoba mi się)
## Low-Rank Factorization (Faktoryzacja niskiego rzędu)
Aproksymacja wag w warstwach za pomocą iloczynu mniejszych macierzy, co zmniejsza liczbę parametrów i operacji.
## Sparsity-inducing regularization
Modyfikacja funkcji kosztu poprzez dodanie kary (np. norma L1 - Lasso), co wymusza dążenie wag do zera podczas treningu