Collezione di dati con organizzazione LIFO
Operazioni:
- isEmpty() -> boolean
- push(elemento)
- pop() -> elemento
- top() -> elemento

Implementazione tramite:
- Array

Riempiamo array da indice 0
Conservo in una variabile l indice di top, cioè l ultimo

```
FUNZIONE isEmpty() -> boolean
IF top==-1 THEN RETURN true
ELSE RETURN false

PROCEDURA push(elemento x)
Top <- top+1
Dati[top] <- x

FUNZIONE top() -> elemento
RETURN dati[top]

FUNZIONE pop() -> elemento
X <- dati[top]
Top <- top-1
RETURN x
```

Pop e top non dovrebbero chiamate se la pila è vuota mentre c e il problema della push se raggiungo il len massimo dell'array
Problema: o creo una array troppo grande sprecando memoria oppure troppo piccolo

- Lista

Primo elemento: elemento che sta in cima, top
Pila vuota rappresentata dalla lista vuota quindi top=null

```
FUNZIONE isEmpty() -> boolean
IF top==null THEN RETURN true
ELSE RETURN false

PROCEDURA push(elemento x)
r <- riferimento a nuovo nodo
r.dato <- x
r.pros <- top
top <- r

FUNZIONE top() -> elemento
RETURN top.dato

FUNZIONE pop() -> elemento
x <- top.dato
top <- top.pros
RETURN x
```

Non abbiamo un limite di capacita
Hanno tempo costante