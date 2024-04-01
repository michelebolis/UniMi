Uno heap/max-heap è un albero binario quasi completo in cui la chiave contenuta in ciascun nodo è maggiore delle chiavi contenute nei figli

Assunzione: abbiamo un max
- Ricerca di elemento di chiave massima: $O(1)$ perché ho già max-heap
- Cancella elemento di chiave massima: $O(\log n)$, vuole dire eliminare la radice e richiamare la procedura risistema dal basso
- Inserimento di un nuovo elemento: elemento aggiunto come ultima foglia (nella prima posizione libera più a sinistra dell’ultimo livello, se non è pieno, oppure come foglia più a sinistra di un nuovo livello) garantendoci cosi di avere sempre un albero completo.
	Sara necessario fare un risistema dal basso in quanto non è garantito la condizione dello heap. Questa procedura confronta il padre della nuova foglia e SE la chiave in esso è minore ne scambio il contenuto continuando finché non ho uno heap.
	Nel caso peggiore si arriva alla radice
	Figlio in posizione x del vettore allora padre=$[\frac{(x-1)}{2}]$
- Cancellare un nodo di chiave x: supponiamo di avere un indice/puntatore all'elemento da cancellare. Per cancellare un elemento lo si può sostituire con la foglia più a destra dell’ultimo livello, che viene rimossa, e poi risistemare lo heap.
- Sia $x$ la chiave del nodo n da cancellare e f la chiave che c era nell'ultima foglia
	- SE $f<x$ ALLORA padre del nodo andrà bene perché è minore di quello precedente MA applico risistema dall'alto perché potrebbe essere piu piccola di uno o di entrambi i figli
	- SE $f>x$ ALLORA f sarà maggiore dei figli del nodo in cui l ho inserita quindi potrebbe essere maggiore della chiave del padre. Applico quindi risistema dal basso dal nodo f
	- In entrambi i casi ho $O(\log n)$
- Modificare la chiave di un elemento: supponiamo di avere un puntatore al nodo da modificare
	- SE chiave viene diminuita: valore della nuova chiave in n è sicuramente minore della chiave del padre. Applico la procedura risistema a partire dal nodo n (faccio scendere il nodo con la chiave aggiornata)
	- SE chiave viene aumentata: valore della nuova chiave in n è sicuramente maggiore anche della chiave del padre n. Applico la procedura risistema dal basso dal nodo n (faccio risalire il nodo con la chiave modificata)
	- In entrambi i casi $O(\log n)$

