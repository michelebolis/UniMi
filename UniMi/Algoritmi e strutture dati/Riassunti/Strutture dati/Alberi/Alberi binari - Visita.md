```
ALGORITMO visitaGenerica(AlberoBinario r)
S <- {r}
WHILE S!=vuota DO
	Preleva un nodo X da S
	Visita X
	S <- S unito {figli di x}
```

- Visita in ampiezza S=coda
```
ALGORITMO visistaInAmpiezza(AlberoBinario r)
C <- coda vuota
C.enqueue(r)
WHILE NOT C.isEmpty() DO
	X <- C.dequeue()
	IF x!=null THEN
		Visita il nodo associato a x
		C.enqueue(x.sx)
		C.enqueue(x.dx)
```

Numero passi proporzionale al numero dei nodi

- Visita in profondita S=pila

```
ALGORITMO visitaInProfondita(AlberoBinario r)
P <- pila vuota
P.push(r)
WHILE NOT P.isEmpty() DO
	X <- P.pop()
	IF x!=null THEN
		Visita nodo associato a x
		P.push(x.dx)
		P.push(x.sx)
```

Albero binario
- Base: albero vuoto
- Induzione: nodo + sottoalbero SX + sottoalbero DX

Ordine di visita
- Ordine anticipato Pre-ordine
```
ALGORITMO visitaInProfondita(AlberoBinario r)
IF r!=null THEN
	Visita la radice
	visitaInProfondita(r.sx)
	visitaInProfondita(r.dx)
```

- Ordine simmetrico In-ordine
```
ALGORITMO visitaInProfondita(AlberoBinario r)
IF r!=null THEN
	visitaInProfondita(r.sx)
	Visita la radice
	visitaInProfondita(r.dx)
```

- Ordine posticipato Post-ordine
```
ALGORITMO visitaInProfondita(AlberoBinario r)
IF r!=null THEN
	visitaInProfondita(r.sx)
	visitaInProfondita(r.dx)
	Visita la radice
```

es
![[Pasted image 20240329142226.png|300]]

Crea notazione postfissa o polacca inversa
SE numero --> push sullo stack
SE segno operazione --> 2 pop sullo stack, i due operandi

```
FUNZIONE nnodi(AlberoBinario r) -> intero
IF r=null THEN RETURN 0
ELSE
	Nsx <- nnodi(r.sx)
	Ndx <- nnodi(r.dx)
	RETURN 1+nsx+ndx
```