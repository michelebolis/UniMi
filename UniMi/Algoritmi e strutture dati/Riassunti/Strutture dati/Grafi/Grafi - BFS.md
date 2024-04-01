Costruisco albero ricoprente

```
ALGORITMO visitaInAmpiezza(grafo G, vertice v)  -> Albero
C <- coda vuota
T <- albero formato solo da s
Marca s come raggiunto
C.enqueue(s)
WHILE NOT C.isEmpty() DO
	u <- C.dequeue()
	FOR EACH (u, v) IN E DO
		IF v non è marcato come raggiunto THEN
			Aggiungi v e (u, v) a T
			Marca v come raggiunto
			C.enqueue(v)
RETURN T
```

- Ciclo while farà $n$ iterazione considerando grafo connesso
- IF interno viene eseguito invece $2m$ volte ogni arco in due direzione
- For each quanto ci costa? Dipende dalla rappresentazione
	Fissato u devo procurarmi tutti gli archi $u, v$
	- Lista di archi --> for each $\Theta(m)$ per ogni iterazione del while --> Tempo $O(n*m)$
	- Lista di adiacenza/incidenza: per ogni vertice so già i vertici connessi --> for each numero passi = numeri vertici adiacenti a $u$. Se sommiamo tutte le iterazioni dell'algoritmo avrò $2m$ passi --> Tempo $O(n+m)$
	- Matrice di adiacenza --> $n$ passi ad ogni iterazione --> Tempo $O(n^2)$
	- Matrice di incidenza --> $m$ passi ad ogni iterazione --> Tempo $O(n*m)$