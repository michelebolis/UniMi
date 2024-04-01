Un albero binario di ricerca è un albero binario in cui per ogni nodo n
- Il valore di ogni chiave contenuta nel sottoalbero sinistro di n è minore della chiave contenuta in n
- Il valore di ogni chiave contenuta nel sottoalbero destro di n è maggiore o uguale alla chiave contenuta in n

Ogni nodo n è composto dalla chiave, da altri campi e da due puntatori sx e dx

![[Pasted image 20240329143418.png|300]]

- Trovare il nodo con chiave max / min
```
FUNZIONE massimo (alberoRicerca r) -> Nodo
IF r=NULL THEN RETURN NULL
ELSE
	n <- r
	WHILE n.dx != NULL D
		N <- n.dx
	RETURN n
```

- Ricerca ricorsiva
```
FUNZIONE trova(alberoRicerca r, tipoChiave k) -> Nodo
IF r=NULL THEN RETURN NULL
ELSE IF k < r.chiave THEN
	RETURN trova(r.sx, k)
ELSE IF k > r.chiave THEN
	RETURN trova(r.dx, k)
ELSE RETURN r
```

- Ricerca iterativa
```
FUNZIONE trova(alberoRicerca r, tipoChiave k) -> Nodo
n <- r
WHILE n!=NULL AND n.chiave!=k DO
	IF k < n.chiave THEN n <- n.sx
	ELSE n <- n.dx
RETURN n
```

- Inserimento ricorsivo
```
FUNZIONE inserisci(alberoRicerca r, elemento d) -> alberoRicerca
k <- d.chiave
IF r=NULL THEN
	r <- riferimento a nuovo nodo
	r.chiave <- k
	r.campi <- d.campi
	r.sx <- NULL
	r.dx <- NULL
ELSE IF k < r.chiave THEN r.sx <- inserisci(r.sx, d)
ELSE r.dx <- inserisci(r.dx, d)
RETURN r
```

- Inserisci iterativo
```
FUNZIONE inserisci(alberoRicerca r, elemento d) -> alberoRicerca
//predispongo nuovo nodo
K <- d.chiave
T <- riferimento a nuovo nodo
t.chiave <- k
t.campi <- d.campi
t.sx <- NULL
t.dx <- NULL

//ricerca posizione
padre <- NULL
n <- r
WHILE n!=NULL DO
	padre <- n
	IF k<n.chiave THEN n <- n.sx
	ELSE n <- n.dx

//inserimento
IF padre=NULL THEN r <- t //albero vuoto
ELSE IF k<padre.chiave THEN padre.sx <- t
	ELSE padre.dx <- t
RETURN r
```

![[Pasted image 20240329143728.png|300]]

- Cancellazione
Cancellazione di un nodo implica la modifica del padre
Sostituisci il contenuto del nodo da cancellare con il contenuto del nodo di chiave piu piccola del sottoalbero dx del nodo da cancellare
Elimina il nodo che aveva chiave piu piccola nel sottoalbero dx
Caso particolare: radice

Negli alberi binari
Sia n numeri dei nodi e h l'altezza
Numero minimo di nodi per alberi di altezza $h$ --> $h+1$
Numero massimo di nodi per alberi di altezza $h$ --> $2^{h+1}-1$
$h+1 <= n <= 2^{h+1}$
$\log_2(n+1) -1 <= h <= n-1$

SE sfruttiamo male altezza, altezza è lineare
SE sfruttiamo l altezza dell'albero, facendo degli alberi completi, l altezza è logaritmica