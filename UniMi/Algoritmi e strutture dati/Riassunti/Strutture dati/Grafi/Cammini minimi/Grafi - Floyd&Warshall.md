Supponiamo $V={v_1, …, v_n}$
$d_{ij}=$ peso del cammino minimo da $v_i$ e $v_j$
Problema Pi determinare $d_{ij}$ con $i=1,…,n$ e $j=1,..,n$
Per $k=0,…,n$, considero il problema vincolato
Problema $P(k)$ determinare $d(k)_{ij}$
$d(k)_{ij}$ = peso del cammino minimo da $v_i$ a $v_j$ che nei passi intermedi visitano esclusivamente vertici di indice $\leq k$
ALLORA $P=P(n)$

Come risolvere $P(k)$
- $k=0$
$$d(k)ij=\begin{cases} w(v_i, v_j) \text{ SE } (v_i, v_j) \in E \cap v_i\neq v_j \\
  0 \text{ SE } v_i=v_j \\
  \infty \text{ ALTRIMENTI } \end{cases}$$
- $k>0$
$d(k)_{ij}= min\{d(k-1)_{ij}, d(k-1)_{ik} + d(k-1)_{kj}\}$ 
//minimo tra percorso diretto i -> j ed un percorso passando da un altro vertice k

```
ALGORITMO FloydWarshall(Grafo G) -> Matrice
Siano D0[1…n, 1…n], …, Dn[1…n, 1…n] matrici
//inizializzo con caso k=0
FOR i <- 1 TO n DO
	FOR j <- 1 TO n DO
	IF i=j THEN D0[i, j] <- 0
	ELSE  IF (vi, vj) appartiene E THEN D0[i, j] <- w(i, j)
	ELSE D0[i, j] <- infinito
//caso k>0
FOR k <- 1 TO n DO
	FOR i <- 1 TO n DO
		FOR j <- 1 TO n DO
		IF Dk-1[i, k] + Dk-1[k, j] < Dk-1[i, j] THEN
			Dk[i, j] <- Dk-1[i, k] + Dk-1[k, j]
		ELSE
			Dk[i, j] <-  Dk-1[i, j]
RETURN Dn
```

$Tempo = O(n^3)$
$Spazio = O(n^3)$

es
![[Pasted image 20240401155421.png]]

Per migliorare lo spazio
So che devo arrivare al massimo fino a k quindi non mi serve avere posizione k
Posso usare la stessa matrice perche i valori $D_{k-1}[i, j]$ e cosi via non cambiano
$d(k)_{ij}= min\{d(k-1)_{ij}, d(k-1)_{ik} + d(k-1)_{kj}\}$
Per $j=k$:  $d(k)_{ik}= min\{d(k-1)_{ik}, d(k-1)_{ik} + d(k-1)_{kk}\} = d(k-1)_{ik}$
Per $i=k$:  $d(k)kj= min{d(k-1)kj, d(k-1)kk + d(k-1)kj} = d(k-1)kj$
QUINDI $D_{k-1}[i, k] + D_{k-1}[k, j] = D_k[1, k] + D_k[k, j]$

```
ALGORITMO FloydWarshall(Grafo G) -> Matrice
Siano D[1…n, 1…n] una matrice
//inizializzo con caso k=0
FOR i <- 1 TO n DO
	FOR j <- 1 TO n DO
		IF i=j THEN D[i, j] <- 0
		ELSE  IF (vi, vj) appartiene E THEN D[i, j] <- w(i, j)
		ELSE D[i, j] <- infinito
//caso k>0
FOR k <- 1 TO n DO
	FOR i <- 1 TO n DO
		FOR j <- 1 TO n DO
			IF D[i, k] + D[k, j] < D[i, j] THEN
				D[i, j] <- D[i, k] + D[k, j]
RETURN D
```

$Spazio = O(n^2)$

Come ricavo il cammino minimo tra $v_i$ e $v_j$
Uso matrice ausiliaria $P$ con $P[i, j]$ massimo indice dei vertici intermedi sul cammino minimo da $v_i$ a $v_j$
Dai valori contenuti alla fine in $P$ si puo ricavare il cammino

```
ALGORITMO FloydWarshall(Grafo G) -> Matrice, Matrice
Siano D[1…n, 1…n] una matrice
//inizializzo con caso k=0
FOR i <- 1 TO n DO
	FOR j <- 1 TO n DO
		IF i=j THEN D[i, j] <- 0
		ELSE  IF (vi, vj) appartiene E THEN D[i, j] <- w(i, j)
		ELSE D[i, j] <- infinito
		P[i, j] <- 0
//caso k>0
FOR k <- 1 TO n DO
	FOR i <- 1 TO n DO
		FOR j <- 1 TO n DO
			IF D[i, k] + D[k, j] < D[i, j] THEN
				D[i, j] <- D[i, k] + D[k, j]
				P[i, j] <- k
RETURN D, P
```

es
![[Pasted image 20240401155518.png]]

Pesi negativi
Es sconti
Cicli negativi --> Non ci sono cammini minimi, problema mal posto
FloydWarshall corretto anche con pesi negativi purché non ci siano cicli negativi

es
![[Pasted image 20240401155529.png]]