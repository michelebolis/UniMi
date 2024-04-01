Problema: Dato G=(V, E) non orientato connesso con una funzione peso w: E -> R trovare un albero ricoprente T=(V, ET) di peso minimo

- Dato $G'=(V, E')$ con $E' \subseteq E$ t.c. $w(G')= \sum_{e \in E'} w(e)$
- $T=(V, E_T)$ è una soluzione del problema SE
	- $T$ è un albero con $E_T \subseteq E$ --> $T$ ammissibile
	- $T'$ albero con $T'=(V, E_{T'}), E_{T'} \subseteq E t.c. w(T) \leq w(T')$ --> T ottima

es
![[Pasted image 20240401151132.png]]

- Strategia [[Tecnica Greedy]]

Inizialmente:
- $T=(V, \emptyset)$
- $C=E$ insieme dei candidati
Ad ogni passo prelevo da $C$ l'arco di peso minimo, lo aggiungo a $T$ SE non forma cicli con gli archi gia scelti

```
ALGORITMO Kruskal(Grafo G=(V, E, w)) -> Albero
Ordina E in maniera non decrescente in base ai pesi
T <- (V, vuoto)
FOR EACH (x, y) IN E secondo l'ordine DO
	IF x e y NON sono connessi in T THEN
		Aggiungi a T l'arco (x, y)
RETURN T
```

Teorema: l'algoritmo di Kruscal trova un albero ricoprente minimo
DIM
T è l'albero trovato da Kruscal
$T_0$ l'albero ricoprente minimo con il maggior numero di archi in comune con T
PER ASSURDO, sia $T_0 \neq T$
Sia (x, y) il primo arco (secondo l'ordine di Kruscal) in T MA non in $T_0$
Essendo $T_0$ un albero ci deve essere un cammino da x a y  
Se ci fosse questo cammino ci sarebbe un ciclo e quindi non sarebbe un albero --> esiste un (u, v) sul cammino t.c. (u, v) non è in T seno avrei un ciclo
Ma allora dato che kruscal va in ordine di peso so che $w(x, y) \leq w(u, v)$
Modifico $T_0$ togliendo (u, v) e aggiungendo (x, y)
Ottengo albero ricoprente $T^-$
$w(T^-)= w(T) - w(u, v) + w(x, y) \leq w(T_0)$
MA allora $w(T_0)$ era minimo e quindi anche $T^-$ è minimo MA $T^-$ ha un arco in piu in comune con T e cio è assurdo per l'ipotesi che $T_0$ sia l'albero ricoprente minimo con piu archi in comune con T  
ho costruito un grafo, come capisco se due vertici sono connessi? Usiamo osservazione che ad ogni passo T è una foresta  quindi abbiamo partizione dei vertici

Implementazione Kruscal
Organizziamo l'insieme dei vertici utilizzando una partizione come struttura ausiliaria
Due vertici appartengono allo stesso elemento della partizione SE E SOLO SE sono connessi da un cammino
x, y sono connessi? --> faccio find dei due elementi e se non sono nella stessa partizione non sono connessi --> UNION
Fasi
- Partizione iniziale: singoletti --> uso MAKESET per ogni vertice
- Ad ogni passo: x e y non sono connessi in T SE E SOLO SE x e y appartengono a insieme differenti --> faccio FIND x e FIND y --> x e y non connessi SE E SOLO SE FIND(x)!=FIND(y)
- Aggiunta di un arco: unione di due elementi delle partizione UNION(x, y)
- Rappresentazione del grafo: lista di archi (array o lista)

```
ALGORITMO Kruscal(Grafo G=(V, E)) -> Albero
Ordina E in maniera non decrescente in base ai pesi
T <- (V, vuoto)
FOR EACH vertice v appartenente V DO makeSet(v)
FOR EACH (x, y) Є E secondo l'ordine DO
	Tx <- FIND(x)
	Ty <- FIND(y)
	IF Tx != Ty THEN
		UNION(Tx, Ty)
		Aggiungi a T l'arco (x, y)
RETURN T
```

Complessità in tempo con [[Partizioni - QuickUnion]] con bilanciamento in altezza
$n=|V|, m=|E|$
1. Ordina E
HeapSort $O(m \log m)$
2. For each per le makeSet
$n$ operazioni makeSet --> $O(1*n)=O(n)$
1. For each sugli archi
$m$ interazioni
$tot FIND = 2m --> O(m*lg 2n)$
$tot UNION = n-1 --> O(1*(n-1))=O(n)$

$O(m \log m) + O(n) + O(m \log n) + O(n) <= O(m \log n^2) + O(m \log n)$ //sapendo che $n^2 \geq m \geq n-1$
$T(m, n) = O(m \log n)$
SE pesi interi potrei usare [[RadixSort]]
SE uso compressione di cammino potrò avere $\log n$ nel FIND

