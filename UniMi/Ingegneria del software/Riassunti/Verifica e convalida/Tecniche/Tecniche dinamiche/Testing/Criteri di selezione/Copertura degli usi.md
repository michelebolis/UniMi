Un test T soddisfa il criterio di copertura degli usi SE e SOLO SE per ogni nodo $i$ e ogni variabile $x \in def(i)$, PER OGNI ELEMENTO $j \in du(x, i)$, T include un caso di test che esegue un cammino libero da definizioni da $i$ a $j$

$T \in C$ SE e SOLO SE $\forall i \in P, \forall x \in def(i), \forall j \in du(x, i), \exists t \in T$ che esegue un cammino da $i$ a $j$ senza definizioni di $x$

`ATT NON implica il criterio di copertura delle definizioni `

[[Copertura degli usi - Esempio]]