Proprieta:
- La soluzione ottima puo non essere all'intersezione dei vincoli
![[Pasted image 20240328164131.png|250]]
- La soluzione ottima puo non essere necessariamente sulla frontiera della regione ammissibile
![[Pasted image 20240328164213.png|250]]

Soluzione ottima locale e globale
In generali gli algoritmi PNL garantiscono solo l ottimalità locale
Una soluzione $x^* \in X$ è un minimo globale SE e SOLO SE 
$$f(x^*) \leq f(x), \forall x \in X$$
Una soluzione $\overline{x} \in X$ è minimo locale SE e SOLO SE
$\exists \epsilon > 0 : f(\overline{x}) \leq f(x), \forall x \in X : ||\overline{x}-x|| \leq \epsilon$
L'insieme delle soluzioni $x \in X : ||\overline{x}-x|| \leq \epsilon$ è un intorno di $\overline{x}$
es le soluzioni $x_1$ e $x_2$ sono ottimi locali mentre $x_3$ è un ottimo globale
![[Pasted image 20240328164435.png|250]]

Per trovare un ottimo globale si dovrebbero enumerare tutti gli ottimi locali e scegliere il migliore
Tuttavia l'enumerazione completa degli ottimi locali in generale non è fattibile in pratica sia per il loro grande numero sia perché non è noto un metodo algoritmico per eseguirla in modo efficiente

Un'importante eccezione positiva è la [[Programmazione convessa]]