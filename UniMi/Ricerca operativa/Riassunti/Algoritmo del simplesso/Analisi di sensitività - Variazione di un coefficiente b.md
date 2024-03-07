Variazione di un coefficiente $b_i$
Intuizione geometrica
![[Pasted image 20240305141026.png|400]]
![[Pasted image 20240305141137.png|200]]
Quando $b_3$ diminuisce, il vincolo 3 trasla verso il basso e a sinistra finche il vincolo 2 diventa attivo con $b_3 = 8$
Quando $b_3$ aumenta, il vincolo 3 trasla verso l'alto e a destra finche il vincolo 1 diventa attivo con $b_4 = 24$

Quindi $B^* = \{1,2,3\}$ è ottima per $8 \leq b_3 \leq 24$
OSS anche se $B^*$ non cambia, $z^*$ e $x^*$ cambiano

Supponiamo di analizzare un problema che nella forma alle disuguaglianze ha 
- funzione obiettivo da massimizzare 
- vincoli di disuguaglianza $\leq$

Considerando una riga $\bar{i}$ e sia la colonna della variabile di slak $\bar{j}$ e $\Delta b_{\bar{i}}$ la variazione possibile
1. $\bar{i} \in B$
$$\max\{-\infty, \max_{i}\{\frac{-b_i^*}{a^{*+}_{i\bar{j}}}\}\} \leq \Delta b_{\bar{i}} \leq \min\{\min_{i}\{\frac{-b_i^*}{a^{*+}_{i\bar{j}}}\} + \infty\}\}$$
Interpretazione: per i valore negativi (numeratore negativi e denominatore positivo) cerchiamo il max mentre di quelli positivi il min, che sono i primi valori che ci fanno cambiare base
2. $\bar{i} \in N$
$$\Delta b_{\bar{i}} \geq -x^*_{\bar{j}}$$
Esempio
![[Pasted image 20240305142038.png|400]]
