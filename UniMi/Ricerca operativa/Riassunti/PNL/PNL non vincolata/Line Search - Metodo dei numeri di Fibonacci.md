Derivative free
[[Line Search - Numeri di Fibonacci]]

Problema
- Data una `funzione continua` $f(x)$ di una sola variabile $x$, si vuole cercare un punto di minimo $f(x)$
- E' dato un `intervallo di incertezza iniziale` $I^0$ ed è richiesto un `massimo intervallo di incertezza finale` $\bigtriangleup$
- Si assume che la `funzione sia unimodale nell'intervallo` $I^0$, cioè abbia `un solo punto di minimo nell'intervallo`
- Si suppone
	- di non poter/voler calcolare la derivata prima di $f(x)$
	- che sia possibile valutare $f(x)$ in punti diversi purché distanti tra loro almeno $\epsilon$ (risoluzione/precisione dell'HW)

OSS sarebbe ancora possibile usare il metodi di bisezione, valutando in ogni intervallo due punti distanti $\epsilon$ posti al centro dell'intervallo stesso MA l informazione sarebbe quella derivante dal calcolo della derivata al centro dell'intervallo
In tal modo sarebbero necessarie due valutazioni della funzione ad ogni iterazione mentre con il metodo di Fibonacci ne basta una

Fasi
- [[Metodo dei numeri di Fibonacci - Iterazione generica]]
- [[Metodo dei numeri di Fibonacci - Intervallo finale]]

Conclusioni
`Il metodo dei numeri di Fibonacci consente di approssimare il minimo di una funzione di una sola variabile continua`. 
`Deve essere noto un intervallo di incertezza iniziale e la funzione deve essere unimodale in esso`. 
Il metodo non richiede il calcolo della derivata prima della funzione. 
Il metodo `richiede di valutare la funzione in un numero di punti dello stesso ordine di grandezza del numero di iterazioni`.

es
Incertezza iniziale $I^0=[0,100]$
E richiesto un massimo intervallo di incertezza finale $\bigtriangleup =2$ 
Risoluzione $\epsilon=1$
![[Pasted image 20240401110147.png|350]]
![[Pasted image 20240401110159.png|350]]
