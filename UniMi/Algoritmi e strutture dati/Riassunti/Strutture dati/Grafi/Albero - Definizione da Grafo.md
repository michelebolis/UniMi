Un albero è un grafo non orientato, connesso e privo di cicli
Una foresta è un insieme di alberi

Fissato un nodo come radice, c'è uno e un solo cammino per un altro vertice

Proprietà: Sia $G=(V, E)$ un albero, il numero degli archi $m=n-1$ ($|E|=|V|-1$)
DIM $n=|V|$
- Base: $n=1$, ho un solo vertice e quindi non ho archi perché se ce lo avessi sarebbe un ciclo --> $m=0$
- Passo: $n>1$, scelgo un $v \in V$ qualunque, rimuovo tutti gli archi adiacenti a $x$. Ottengo una foresta di alberi, chiamo $G_1=(V_1, E_1), …, G_k=(V_k, E_k)$ gli alberi ottenuti da $G$ rimuovendo $x$ e gli archi incidenti su $x$.
	ALLORA $k =$ numero di archi incidenti su $x$. Per $i=1,…k$ $|V_i|<|V|$ -> ipotesi $|E_i|=|V_{i-1}|$.
	$|E|=|E_1|+…+|E_k+k| = |V_1| -1 + … |V_{k-1}| +k = |V_1|+ … + |V_k| = |V| -1$ //perché -1 sarebbe x che ho tolto

Sia $G=(V, E)$ non orientato e connesso
SE $|E|=|V|-1$ ALLORA $G$ è un albero

DIM per assurdo
Sia $G$ non orientato, connesso $|E|=|V|-1$ e $G$ NON albero
SE non è un albero vuol dire che ha un ciclo
Continuo a eliminare archi in modo che il grafo rimanga connesso e non ci siano piu cicli
Ottengo $G'=(V', E') |E'|<|E|, V'=V$ rimane connesso e privo di cicli
QUINDI $G'$ è un albero MA ALLORA dato che $|E'|=n-1$ abbiamo che $n-1<n-1$ ASSURDO

Teorema Un grafo $G=(V, E)$ non orientato e connesso è un albero SE E SOLO SE $|E|=|V|-1$

Dato $G=(V, E)$ un grafo non orientato connesso

Un albero di supporto o ricoprente o Spanning Tree di $G$ è un albero $G'=(V', E')$ con $V'=V$ e $E' \subseteq E$
Avendo $|V|$ devo ottenere $|E|=|V|-1$