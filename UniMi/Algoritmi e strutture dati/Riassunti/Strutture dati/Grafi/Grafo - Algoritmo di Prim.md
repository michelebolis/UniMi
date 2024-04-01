Fasi
- Inizialmente: $T$ è costituito da un unico vertice
- Ad ogni passo: espando $T$ aggiungendo l'arco $(x, y)$ di peso minimo con un vertice in $T$ e l'altro non in $T$

```
ALGORITMO Prim(Grafo G=(V, E)) -> Albero
T <- albero costituito da un unico vertice qualsiasi
WHILE T ha meno di n vertici DO
	Sia (x, y) l'arco di peso minimo con x in T e y NON in T
	Aggiungi a T il vertice y e l'arco (x, y)
RETURN T
```

Teorema: Prim trova sempre la soluzione ottima

es
![[Pasted image 20240401152900.png]]


Implementazione Prim
Ad ogni passo per ogni vertice v non ancora in T consideriamo
- $d[v]$ = minimo peso degli archi tra $v$ ed i vertici in $T$
- $d[v] = min\{w(u, v) | u \in V_T\} \cup \{\infty\}$
- $vicino[v] = u \in T$ t.c. $d[v]= w(u, v)$

Quando aggiungo un vertice aggiorno la tabella guardando gli archi uscenti e paragonandone il peso con quello della tabella modificandolo solo se il nuovo vertice ha un peso inferiore
Come trovare elemento minimo:
- Scandire tutta la tabella --> $O(n)$
- Usare anche una coda con priorità che ha come chiave il valore di $d[v]$. Posso prelevare elemento con priorità massima che è la chiave minima $O(\log n)$

```
ALGORITMO Prim(Grafo G=(V, E, w)) -> Albero
Sia C una coda con priorità vuota
Sia d e vicino due array con indici di V
//Inizialmente
FOR EACH v appartenente V DO
	d[v] <- infinito //ogni vertice v ha priorità d[v]=infinito
	C.insert(v, infinito)
T <- (vuoto, vuoto)
//ad ogni passo
DO
	Y <- C.deleteMin() //preleva vertice y con d[y] minima
	VT <- VT U {y}
	IF d[y] != infinito THEN
		X <- vicino[y] //aggiungo a T il vertice y e l'arco (x, y) con x=vicino[y]
		ET <- ET U {(x, y)}
	FOR EACH (y, z) Є E DO
		IF z !Є VT AND w(y, z) < d[z] THEN
			d[z] <- w(y, z)
			C.changeKey(z, w(y, z))
			vicino[z] <- y
WHILE C!=vuoto
RETURN T
```

- Rappresentazione di $G$: liste di adiacenza
- Coda con priorità $C$: heap di $n$ elementi (vettore posizionale)

Analisi tempo
1. For each per riempire la coda = riempire array, $O(n)$
2. DO WHILE farà n iterazioni
DeleteMin() avrà $O(n \log n)$
Operazioni nel primo IF possiamo assumere O(1) --> $O(n)$
3. For each farà in totale $2m$ perché ogni arco verrà ispezionato da entrambi i versi
ChangeKey è al massimo $m$ --> $O(m \log n)$
Mentre le altre hanno tempo costante

$O(n) + O(n \log n) + O(n) + O(m \log n) = O(m \log n)$ //stesso motivo di prima
$T(n, m) = O(m \log n)$

Heap di Fibonacci si implementa changeKey con $O(1)$ ammortizzato SE la chiave diminuisce
Grazie a ciò $T(n, m) = O(m + n \log n)$
Questo è migliore se $m$ è basso non vicino a $n^2$
