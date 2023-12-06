- $ok(T,P)$
L'esecuzione di un test consiste nell'esecuzione del programma $\forall t \in T$
Un programma passa o supera un test:$$ok(P, T) <-> \forall t \in T, ok(P,t)$$
- $successo(T,P)$
Un test ha successo SE rileva uno o piu malfunzionamenti (non ancora noti) presenti nel programma P
$$successo(T, P) <-> \exists t \in T, !ok(P, t)$$

[[Test ideale]]