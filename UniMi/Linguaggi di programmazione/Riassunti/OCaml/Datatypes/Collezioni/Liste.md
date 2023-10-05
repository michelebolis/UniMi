Le liste sono $omogenee$
L'operatore di concatenazione è @ MA è inefficiente, meglio usare il costruttore in testa e poi invertire 

Sintassi:
 ```ocaml
let l = [valore1; valore2]
```
sul pattern matching non posso usare stringhe ma posso sulle liste perché ho un costruttore 

es contare il numero di occorrenze
 ```ocaml
let count x l = 
	let rec count tot x = function 
		[] -> tot 
		| h::tl -> if (h==x) then count (tot+1) x tl else count tot x tl 
	in count 0 x l
 ```
Notare che $l$ è usata implicitamente in  `count` e nella sua definizione, ma notiamo come venga passata negli argomenti di count.

Si è utilizzato poi la sintassi:
 ```ocaml
let var = expression1 in expression2
  ```
Questo è il modo in OCaml per definire variabili locali
In questo caso quindi userò `var` in `expression2` e se apparirà in `expression1`