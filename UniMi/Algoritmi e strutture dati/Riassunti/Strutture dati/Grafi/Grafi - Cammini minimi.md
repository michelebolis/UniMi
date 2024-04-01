[[Programmazione dinamica]]

$G(V, E)$ grafo orientato
$w: E --> R$ funzione peso
$c=<v_0, …, v_k>$ t.c. esiste arco da $v_{n-1}$ a $v_n$
$w(c) = \sum_{i=1}^{k} w(v_{i-1}, …, v_i)$ peso del cammino

$c^*$ è un cammino minimo da $x$ a $y$ SE
- $c^*$ è un cammino da $x$ a $y$
- Per ogni cammino $c$ da $x$ a $y$, $w(c) \geq w(c^*)$

Proprietà: principio di ottimalità
Per ottenere soluzione ottima combino soluzioni ottime
SE tutti i pesi sono positivi ALLORA ogni cammino minimo è semplice
SE ci sono pesi negativi MA NON ci sono cicli di peso negativo ALLORA se esiste cammino da x a y ALLORA esiste un cammino minimo da x a y semplice

Rappresentazioni:
- Lista di adiacenza con pesi
	![[Pasted image 20240401154216.png]]
- Matrice dei pesi
	- $\infty$ SE non c'è l arco
	- Peso dell'arco ALTRIMENTI
	![[Pasted image 20240401154229.png]]

Problemi associati:
- Cammino minimo tra due vertici: NON ho algoritmi diretti
- Cammini minimi da un vertice a tutti gli altri
	- [[Grafi - Algoritmo di Dijkstra]] SE non ho pesi negativi. $O(m \log n)$ / $O(m + n \log n)$
	- [[Grafi - Bellman&Ford]]: SE non ho cicli negativi. $O(m n)$
- Cammini minimi tra ogni coppia di vertici
	- [[Grafi - Floyd&Warshall]]: SE non ho cicli negativi. $O(n^3)$
SE cicli negativi --> problema mal posto