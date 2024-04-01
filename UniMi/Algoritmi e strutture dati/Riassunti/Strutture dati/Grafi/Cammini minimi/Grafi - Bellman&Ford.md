INPUT $G=(V, R), w: E --> R$
$v \in V$ vertice di partenza

$d[v]=$ peso del cammino minimo da $s$ a $v$ sinora trovato
Inizialmente
$$d[v]= \begin{cases} 0 \text{ SE } v=s \\
\infty ALTRIMENTI \end{cases}$$

Ad ogni passo si seguono tutti i possibili archi
```
IF d[u] + w(u, v) < d[v] THEN
	d[v] <- d[u] + w[u, v]
```
Questo viene fatto $n-1$ volte
Ipotesi G privo di cicli negativi
QUINDI tra ogni coppia di vertici esiste un cammino minimo semplice
E' sufficiente considerare cammini composti al massimo da $n$ vertici quindi da $n-1$ archi

```
ALGORITMO Bellman&Ford(Grafo G, vertice s) -> vettore
Sia d[v] un vettore con indici in V
d[s] <- 0
FOR EACH v Є V \ {s} DO d[v] <- infinito
FOR k <- 1 TO n-1 DO
	FOR EACH (u, v) Є E DO
		IF d[u] + w(u, v) < d[v] THEN
			d[v] <- d[u] + w(u, v)
RETURN d
```

Analisi tempo
Rappresentazione: lista degli archi
- Primo for each fa $n$ iterazioni: $O(n)$
- Secondo for fa $n-1$ iterazioni
	- For each interno fa $m$ iterazioni
In totale quindi $O((n-1)*m)=O(nm)$

$T(n, m)= O(n)+O(nm)=O(nm)$
SE pochi archi --> tempo quadratico
SE molti archi --> tempo cubico