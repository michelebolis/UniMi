INPUT $G=(V, R), w: E --> R$
$s \in V$ vertice di partenza

$d[v]=$ peso del cammino minimo da $s$ a $v$ sinora trovato
Modifica di $d[v]$ analoga a Bellman MA scelgo un vertice $u$ con una strategia greedy t.c. abbia distanza provvisoria minima, e da li considero tutti gli archi uscenti
Ipotesi: pesi non negativi

Strategia greedy: preleva da $C$ il vertice $u$ con $d[u]$ minimo, $d[u]$ diventa definitivo aggiorno $d[v]$ per ogni $v$ adiacente a $u$

```
ALGORITMO Dijkstra(Grafo G, vertice s) -> vettore
Sia d[v] un vettore con indici in V
d[s] <- 0
FOR EACH v Є V \ {s} DO d[v] <- infinito
C <- V
WHILE C!=vuoto DO
	u <- elemento di C con d[u] minimo //scelta greedy
	C <- C \ {u}
	FOR EACH (u, v) Є E DO 
		//in questo caso u è fissato, non lo faccio su ogni vertice
		IF d[u] + w(u, v) < d[v] THEN
		d[v] <- d[u] + w(u, v)
RETURN d
```

Si può dimostrare che ogni volta che viene valutata la condizione del ciclo WHILE
- $\forall v \in C, d[v]=$ la lunghezza del cammino minimo da $s$ a $v$ che prima di raggiungere v visita solo vertici non in $C$
- $\forall v \notin C, d[v]=$ lunghezza del cammino minimo da $s$ a $v$
L'algoritmo trova sempre la soluzione corretta

Rappresentazione: lista di adiacenza o incidenza
Per trovare il minimo usiamo la coda con priorità come struttura di supporto

```
ALGORITMO Dijkstra(Grafo G, vertice s) -> vettore
Sia d[v] un vettore con indici in V
d[s] <- 0
FOR EACH v appartenente V \ {s} DO d[v] <- infinito
Sia C una coda con priorità vuota
FOR EACH v Є V DO C.insert(v, d[v])
WHILE C!=vuoto DO
	u <- C.deleteMin() //scelta greedy
	FOR EACH (u, v) Є E DO 
	//in questo caso u è fissato, non lo faccio su ogni vertice
	IF d[u] + w(u, v) < d[v] THEN
		d[v] <- d[u] + w(u, v)
		C.changeKey(v, d[v])
RETURN d
```

  
Analisi tempo
Rappresentazione: lista di adiacenza
Coda con priorità <-> Min-heap <-> vettore posizionale
- Primo for each n iterazioni $O(n)$
- Secondo for each $n$ operazioni di insert $O(n*\log n)$ MA sapendo che è implementata con vettore posizionale in realtà l'elemento 0 sarà s quindi $O(n)$
- While fa $n$ iterazioni
	- deleteMin viene eseguita n volte ed ha costo $O(\log n)$ quindi $O(n*\log n)$
	- For each viene eseguito in totale $m$ volte
		- IF eseguito $m$ volte e changeKey viene eseguito al massimo $m$ volte,$O(\log n)$ --> $O(m*\log n)$

$T(n, m)= O(n)+O(n*\log n)+O(n)+O(n*\log n)+O(m*\log n)$
$= O(n*\log n)+O(m*\log n)= O(m*\log n)$
//$n-1<=m<=n^2$
SE usiamo un heap di fibonacci otteniamo un costo di $O(m + n*\log n)$

Per trovare il cammino minimo mi salvo durante l'algoritmo delle informazioni
Vettore dei predecessori $prod[v]$
$prod[v]$ <- u //Lo metto dentro l IF

Dimenticandoci delle direzioni degli archi otteniamo un albero con radice, albero dei cammini minimi
SE applico Dijkstra su un grafo non orientato, l'albero ricoprente minimo è diverso dall'albero dei cammini minimi perché in quello ricoprente dobbiamo minimizzare il peso dell'albero mentre nell'albero dei cammini dobbiamo minimizzare il peso dei cammini, sono due problemi di ottimizzazione diversi

Supponiamo di avere pesi negativi, allora l'algoritmo di Dijkstra fallisce

es
![[Pasted image 20240401160530.png]]