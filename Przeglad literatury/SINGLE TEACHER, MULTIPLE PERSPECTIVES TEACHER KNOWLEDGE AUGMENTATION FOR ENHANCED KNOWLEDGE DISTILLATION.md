https://openreview.net/pdf?id=DmEHmZ89iB
Praca ta stara się zaadresować sytuację, w której derstylacja z wielu nauczycieli lub nauczyciela i asystentów daje lepsze wyniki, jednak wymaga wytrenowania wielu sieci w pierwszej kolejności.
Autorzy stawiają więc kluczowe pytanie: **Czy możemy uczyć studenta z wykorzystaniem różnorodnych perspektyw, używając do tego tylko jednego nauczyciela?**
Autorzy wprowadzają innowacyjną metodę o nazwie **TeKAP** (Teacher Knowledge Augmentation via Perturbation). Zamiast trenować wielu nauczycieli, TeKAP generuje syntetyczne, zróżnicowane perspektywy na podstawie jednego, wstępnie wytrenowanego modelu nauczyciela.
Osiąga się to poprzez wstrzykiwanie losowego szumu (perturbacji) na dwóch poziomach:

- **Perturbacje na poziomie cech (Feature-level):** Do map cech nauczyciela dodawany jest szum Gaussa. Dzięki temu uczeń poznaje szersze spektrum wariancji i różnorodnych reprezentacji, co działa jak silna regularyzacja (podobnie do mechanizmu dropout). Przekształcenie to opisuje wzór fT(i)​(x)=α×ηi​+(1−α)×fT​(x).    
- **Perturbacje na poziomie logitów (Logit-level):** Szum dodawany jest również do logitów (aktywacji po funkcji softmax). Zmienia to relacje międzyklasowe (tzw. "dark knowledge"), co zmusza model ucznia do lepszej generalizacji zamiast overfittingu do jednego sztywnego zestawu logitów. Odpowiada za to równanie zT(i)​(x)=α×ηi​+(1−α)×zT​(x).
Warto zauważyć, że prezentowane podejście jest architecture agnostic.
# Wyniki
![[Pasted image 20260330152821.png]]


#Destylacja #Architecture_agnostic #Y2025 