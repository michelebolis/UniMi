$def(i)$ è l'insieme delle variabili che sono definite in $i$
$du(x, i)$ è l'insieme dei nodi $j$ t.c.:
- $x \in def(i)$
- $x$ è usato in $j$
- esiste un cammino da $i$ a $j$ libero da definizioni di $x$

Un test T soddisfa il criterio di copertura delle definizioni SE e SOLO SE **per ogni nodo $i$ e ogni variabile $x \in def(i)$, T include un caso di test che esegue un cammino libero da definizioni da $i$ ad almeno uno degli elementi di $du(x, i)$**

$T \in C$ SE e SOLO SE $\forall i \in P, \forall x \in def(i), \exists j \in du(x,i), \exists t \in T$ che esegue un cammino da $i$ a $j$ senza definizioni di $x$

[[Copertura delle definizioni - Esempio]]
