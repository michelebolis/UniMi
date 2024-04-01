Uno heap/max-heap è un albero binario quasi completo in cui la chiave contenuta in ciascun nodo è maggiore delle chiavi contenute nei figli

OSS per comodità consideriamo heap in cui le foglie dell'ultimo livello si trovano piu a sinistra

Proprietà: chiave piu grande sarà alla radice
Strategia di promozione ha il problema che potrei non ottenere piu lo heap cioè albero quasi completo

Promuovo l'ultima foglia da destra

Ipotesi Heap con radice non ordinata
```
PROCEDURA risistema/fixHeap(Heap H)
V <- H //V nodo in esame
X <- V.chiave
Y <- V.altriCampi
deallocare <- true
DO
	IF V è una foglia THEN
		deallocare <- false
	ELSE
		U <- figlio di V con valore max
		IF u.chiave > X THEN
			V.chiave <- U.chiave
			V.altricampi <- U.altricampi
			V <- U
		ELSE
			deallocare <- false
WHILE deallocare
V.chiave <- X
V.altricampi <- Y
```

Numero Confronti $\Theta(h)=\Theta(\log_2 n)$

es
![[Pasted image 20240329132040.png]]

[[HeapSort - Miglioramenti]]
[[HeapSort - Analisi Temporale]]

Implementazione in loco: riempio i nodi dell'albero leggendo gli elementi dell'albero da sx a dx, stiamo facendo una visita in ampiezza per riempire l albero

Elemento di indice i avrà figli in posizione $2i+1$ e $2i+2$
Vettore posizionale
es
![[Pasted image 20240329133123.png]]

So che radice dello heap si trova sempre alla posizione 0
Uso indice $L$ per indicare la posizione in cui inizia la parte ordinata
Quando faccio lo scambio lo faro con l'elemento in posizione $L-1$
L'array cosi sarà diviso in due parti: da $L$ ho la parte riordinata mentre prima ho l albero ancora da riordinare

```
PROCEDURA risistema(Array A[0…N-1], intero r, intero L)
V <- r // V posizione in esame
X <- A[v] // X chiave da sistemare
daCollocare <- true
DO
	IF 2*V + 1 >= L THEN
		daCollocare <- false
	ELSE
		u <- 2*u+1
		IF u+1<L AND A[u+1] > A[u] THEN
			u <- u+1
			IF A[u] > X THEN
			A[V] <- A[u]
			V <- u
		ELSE
			daCollocare <- false
WHILE daCollocare
A[V] <- X

PROCEDURA creaHeap(Array A[0…N-1])
FOR i <- [n/2] DOWN TO 0 DO
	risistema(A, i, n)

ALGORITMO heapSort(Array A[0…N-1])
creaHeap(A)
FOR L <- l-1 DOWN TO 1 DO
	Scambia A[0] con A[L]
	risistema(A, 0, L)
```

Riassumendo:
- È un algoritmo di ordinamento in loco, infatti non uso memoria aggiuntiva
- Numero confronti: $\Theta(n*\log n)$
- Tempo: $\Theta(n*lg n)$ SE i CFR sono $O(1)$
- Metodo NON stabile
	![[Pasted image 20240329133455.png]]

