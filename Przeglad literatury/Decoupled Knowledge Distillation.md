https://arxiv.org/pdf/2203.08679

Autorzy udowodnili matematycznie, że klasyczne DKL z destylacji Hintona można rozbić na dwie składowe:
- TCKD (Target Class Knowledge Distillation) - Transfer wiedzy o tym jak bardzo poprawna klasa dominuje nad innymi klasami
- NCKD (Non-Target Class Knowledge Distillation) - Transfer wiedzy o relacjach między błędnymi klasami, dark knowledge.
Normalnie te atrybuty są powiązane (u Hintona). Postulują, że waga NCKD jest wprost proporcjonalna do wartości $(1-p_t)^2$ więc uważają żę duże $p_t$ prowadzi do utraty czarnej wiedzy. Co jest bez sensu bo po to jest temperatura u Hintona, jeżeli to $p_t$ jest duże to po prostu obiekt tej klasy nie jest podoby do innych, jedyna zasadność tego jest w sytuacji kiedy tracimy jakąś ogólną zależność nie związaną z tym przykładem miedzy klasami. W myśl NCKD obserwacja jest zagajeniem do dyskusji między klasami, ale nie jest jej tematem.
Jako rozwiązanie proponują rozbicie funkcji na dwa komponenty
$$DKD = \alpha \cdot TCKD + \beta \cdot NCKD$$
I dodaje współczynniki $\alpha$ i $\beta$ które mają pozwolić na przypisanie wagi konkretnym częścią.



#Destylacja #Y2022 