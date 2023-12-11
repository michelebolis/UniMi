Un test T soddisfa il criterio di copertura degli usi SE e SOLO SE per ogni nodo i e ogni variabile x \in def(i), PER OGNI ELEMENTO j \in du(x, i), T include un caso di test che esegue un cammino libero da definizioni da i a j

$T \in C$ SE e SOLO SE $\forall i \in P, \forall x \in def(i), \forall j \in du(x, i), \exists t \in T$ che esegue un cammino da $i$ a $j$ senza definizioni di $x$

es
![[Pasted image 20231211094809.png|300x400]]

Considerando la variabile a:
$du(a, 5) = \{7, 8, 9, 11, 12\}$
$du(a, 9) = \{7, 8, 9, 11, 12\}$

![[Pasted image 20231211095048.png]]

T = {<4, 8>, <12, 8>, <12, 4>}