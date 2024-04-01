Collezione di dati con organizzazione FIFO
Operazioni
- isEmpty() -> boolean
- enqueue(elemento)
- dequeue() -> elemento
- first() -> elemento

Implementazione tramite
- Array

Due indici che puntano rispettivamente al primo e all ultimo elemento
Difetti: array ha capacita limitata e una volta che prelevo un elemento devo spostare tutti gli altri elementi

- Liste

Due puntatori che puntano al primo e all ultimo elemento
Per l'inserimento, che avviene in coda, usiamo l ultimo mentre per il dequeue uso il primo
SE coda vuota, primo=ultimo=null

```
FUNZIONE isEmpty() -> Boolean
If primo=null THEN return true
ELSE return false

FUNZIONE first() -> elemento
RETURN primo.dato

FUNZIONE dequeue() -> elemento
X <- first()
primo <- primo.pros
IF primo=null THEN ultimo <- null
RETURN x
```

Tempo indipendente dalla lunghezza della coda

```
PROCEDURA enqueue(elemento x)
R <- riferimento a un nuovo nodo
r.dato <- x
r.pross <- null
IF primo=null THEN //coda vuota
	Primo <- r
	Ultimo <- r
ELSE
	Ultimo.pros <- r
	Ultimo <- r
```

Tempo costante