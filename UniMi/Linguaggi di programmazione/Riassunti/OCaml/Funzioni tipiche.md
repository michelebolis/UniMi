- map: per applicare una funzione a tutti gli elementi di una lista

```ocaml
let rec map f = function 
	h::l1 -> f h::map f l1 
	| _ -> [];;
```

- filter: filtrare fuori gli elementi secondo un predicato

```ocaml
let rec filter p = function
	[] -> [] 
	| h::l -> if p h then h :: filter p l else filter p l
```

- reduce: aggregare secondo un operazione. In OCaml si chiama folding, c è right_fold e left_fold 

```ocaml
let rec reduce acc op = function 
	[] -> acc 
	| h::tl -> reduce (op acc h) op tl ;;
```

Da queste si possono definire
- exists che restituisce true SE almeno un elemento rispetta il predicato

```ocaml
let exists p l = reduce false (||) (map p l);;
```

- forall che restituisce true SE tutti gli elementi rispettano il predicato

```ocaml
let forall p l = reduce true (&&) (map p l);;
```
