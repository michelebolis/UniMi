1 chiamata di risistema per ogni nodo
Risistema fa $Ο(\log_2 n)$
Quindi faro $Ο(n*\log_2 n)$

Analisi migliorata:
Fissiamo la profondita $p$
Risistema su un nodo a profondita $p$ farà $\Theta(h-p)$ passi
A profondita $p$ ci sono $2p$ nodi
QUINDI $\Theta(2^p *(h-p))$ passi

$$\sum_{p=0}^{h}{2^p *(h-p)} = \sum_{p=0}^{h} h*2^p - \sum_{p=0}^{h} p*2^p =$$
$$h*(2^{h+1} -1) - (h-1)*2^{h+1} -2 = +h*2^{h+1} -h -h*2^{h+1} +2^{h+1} -2 = 2^{h+1} -h-2$$
$h \approx \log_2 n$
$2^{\log_2 n +1} -2 = \Theta(n)$

```
ALGORITMO heapSort(Array A) -> lista
Crea heap H a partire da A //comprende trasformare A in un albero quasi completo+creaHeap(A)
X <- lista vuota
WHILE H!=vuoto DO
	Rimuovi da H il valore della radice e aggiungilo all inizio di X
	Rimuovi l ultima foglia (a destra) di H e collocane il valore alla radice
	Risistema(H)
```

Numero Confronti: $\Theta(n) + O(n*\log n) = O(n*\log n)$ //creaHeap + n iterazioni * risistema(H)