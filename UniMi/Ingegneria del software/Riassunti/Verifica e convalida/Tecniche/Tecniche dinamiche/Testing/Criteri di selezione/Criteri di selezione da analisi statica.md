L'analisi statica del codice porta a nuovi criteri di copertura

$def(i)$ è l'insieme delle variabili che sono definite in $i$
$du(x, i)$ è l'insieme dei nodi $j$ t.c.:
- $x \in def(i)$
- $x$ è usato in $j$
- esiste un cammino da $i$ a $j$ libero da definizioni di $x$

Un test T soddisfa il criterio di copertura delle definizioni SE e SOLO SE **per ogni nodo $i$ e ogni variabile $x \in def(i)$, T include un caso di test che esegue un cammino libero da definizioni da $i$ ad almeno uno degli elementi di $du(x, i)$**

- [[Copertura delle definizioni]]
- [[Copertura degli usi]]
- [[Copertura dei cammini DU]]
- [[Copertura del budget]]