Ipotesi albero binario quasi completo --> voglio ottenere un heap
- Soluzione 1: divide et impera, top-down
Albero vuoto: è già un heap
Albero non vuoto: risolvo prima sul sottoalbero di sx, poi su quello di dx e combino le soluzioni
L'unico fuori posto può essere la radice che risolviamo con risistema

```
PROCEDURA creaHeap(albero T)
IF T!=albero vuoto THEN
	creaHeap(T.sx)
	creaHeap(T.dx)
	Risistema(T)
```

Problema: soluzione usa lo stack

es
![[Pasted image 20240329132118.png|300]]

- Soluzione 2: partiamo dalle foglie, bottom-up
Supponiamo l'accesso ai singoli nodi
Trasformo ogni foglia in uno heap chiamando risistema sull'albero con radice il nodo che sto sistemando

```
PROCEDURA creaHeap(Albero T)
h <- altezza di T
FOR p <-h DOWNTO 0 DO
	FOREACH nodo X di profondità p DO
		Risistema(sottoalbero di radice X)
```

es
![[Pasted image 20240329132149.png|300]]
