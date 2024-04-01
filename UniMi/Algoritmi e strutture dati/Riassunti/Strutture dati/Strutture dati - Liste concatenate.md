E' una lista lineare formato da un insieme ordinato di nodi collegati linearmente uno dopo l'altro

Ogni nodo contiene
- Un dato della collezione formato da vari campi e una chiave
- L informazione per accedere al nodo successivo

Accesso ai nodi avviene tramite riferimento, puntatori
x = riferimento al nodo
x.chiave = valore chiave
Non è detto che il prossimo elemento ci sia --> indicheremo come null=riferimento nullo
x <- x.pros //assegno il puntatore successivo

I nodi possono essere memorizzati in porzioni di memoria non contigua
Ottengo flessibilità ma perdo l accesso diretto

- Ricerca elemento in base all'indice
Per accedere all'elemento di posto i, il tempo è proporzionale a i, caso peggiore tempo=lunghezza lista

```
FUNZIONE elemento(Lista L, indice i) -> Nodo
p <- L
WHILE (p!=null AND i>0) DO
	p <-p.pros
	i <- i-1
RETURN p
```

- Ricerca elemento in base alla chiave

```
FUNZIONE trova(Lista L, tipoChiave k) -> Nodo
p <- L
WHILE (p!=null AND p.chiave!=k) DO
	p <-p.pros
RETURN p
```

- Ricerca elemento in base alla chiave in una lista ordinata

```
FUNZIONE trova(Lista L, tipoChiave k) -> Nodo
p <- L
WHILE (p!=null AND p.chiave<k) DO
	p <-p.pros
	IF p=null OR p.chiave>k THEN
		RETURN null
	ELSE
		RETURN p
```

Tempo resta sempre $\Theta(n)$

- Inserimento in lista ordinata mantenendo l ordine

```
FUNZIONE inserisci (ListaOrdinata L, elemento d) -> ListaOrdinata
k <- d.chiave
p <- L
prec <- null
WHILE p!=null AND p.chiave<k DO
	prec <- p
	p <- p.pros
r <- riferimento ad un nuovo nodo
r.chiave <- k
r.altriCampi <- d.altriCampi
r.pros <-p
IF prec !=null THEN
	prec.pros <- r
ELSE
	L.pros <- r
RETURN L
```

Costo inserimento=costo ricerca=$\Theta(n)$

Implementazione tramite array
Implementazione tramite puntatori