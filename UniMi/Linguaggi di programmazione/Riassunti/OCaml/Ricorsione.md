Una funzione è ricorsiva quando è definita attraverso se stessa, specificando un caso base e un passo induttivo.
In OCaml devo esplicitare quando una funzione è ricorsiva con la keyword $rec$

 ```ocaml
let rec fact(n) = if n<=1 then 1 else n*fact(n-1)
 ```


All'invocazione di una funzione viene creato un record di attivazione/frame utilizzato per salvare il valore delle variabili locali, parametri, valore di ritorno...
essendo impilati, l'argomento e il valore di ritorno sono in posizioni note, in particolare il valore di ritorno e l'argomento sono in alto e in basso

La soluzione iterativa è spesso piu complessa ma piu efficiente in quanto non crea un record di attivazione ad ogni passo.

ottimizzazione possibile: memorization/caching

Il problema è che mi serve l $n$ precedente, un dato locale, per questo mi serve un record di attivazione 
Per evitare l'overhead utilizziamo la ricorsione in coda, accumulando in un ulteriore argomento tutto

es
 ```ocaml
let rec trfiboaux n m fib_m' fib_m = 
	if (n=m) then fib_m else (trfiboaux n (m+1) fib_m (fib_m'+fib_m));; 
	let fibo n = if n<=1 then 1 else trfiboaux n 1 0 1;;
```
