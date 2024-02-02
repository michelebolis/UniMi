Un test `T` per un programma `P` è un sottoinsieme (finito) di `D`
Un elemento `t` di un test `T` è detto `caso di test`
L'esecuzione di un test consiste nell'esecuzione del programma $\forall t \in T$

Un programma passa o supera un test:$$ok(P, T) <-> \forall t \in T, ok(P,t)$$
Un programma è corretto per un test SE per ogni $t \in T$, P è corretto

Un test ha successo SE rileva uno o piu malfunzionamenti (non ancora noti) presenti nel programma P
$$successo(T, P) <-> \exists t \in T, \neg ok(P, t)$$

[[Test ideale]]