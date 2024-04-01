Matrice quadrata booleana $n*n$
$M[u, v]= 1$ SE esiste arco da $u$ a $v$
Grafo non orientato: arco rappresentato due volte --> matrice simmetrica
- Riga $i$ ci dice gli archi uscenti da $i$
- Colonna $i$ ci dice gli archi entranti da $i$

$Spazio = \Theta(n^2)$

Vantaggi: comodo per certe manipolazioni
Svantaggi: se matrice densa non ho molti vantaggi rispetto alla rappresentazione precedente mentre SE ho $m=O(n)$ il grafo è sparso e non conviene

$M^2$ = significa seguire due archi, quindi dalla riga $i$ posso andare al vertice rappresentato dalla colonna $j$
// con + faccio OR e * faccio AND
Generalizzando $M^k [i, j]=1$ SE esiste cammino di lunghezza $k$ da $i$ a $j$

es
![[Pasted image 20240401145610.png|300]]
