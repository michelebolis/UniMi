Il polimorfismo permette di gestire diversi tipi usando un interfaccia uniforme
- Polimorfismo di funzione: una funzione che puo valutare è essere applicata a valori di diversi tipi
- Polimorfismo di data type: un data type che puo essere un tipo generalizzato

OCaml supporta nativamente il polimorfismo 

Tassonomia
- Ad Hoc Polymorphism: le funzioni denotano diverse implementazione in base ai tipi o alle loro combinazioni. Supportato in molti linguaggi dall'overloading

- Polimorfismo parametrico: tutto il codice è scritto senza menzionare un tipo specifico. E' supportato dall'uso di generici o template

OCaml supporta nativamente il polimorfismo parametrico
es
```ocaml
let compose f g x = f (g x);;
(* val compose : ('a -> 'b) -> ('c -> 'a) -> 'c -> 'b = <fun> *)
let compose' = compose (fun c -> int_of_char c) ;;
(* val compose' : ('_a -> char) -> '_a -> int = <fun> *)
```

\_ significa che il tipo è debole, è polimorfo ma non piu generico ma è stato legato da qualcosa
In particolare nell'es $'a$ era generico in `compose`, ma in `compose'` diventa weaked in quanto `int_of_char` richiede che 'a sia un `int`

Niente che sia il risultato di una applicazione di una funzione a un argomento puo essere polimorfo
`'a` significa qualsiasi tipo
`'_a'` significa che esiste SOLO un tipo t.c.

- Subtype polimorfismo: restringe il range di tipi che puo essere usato in un caso di polimorfismo parametrico. Realizzato con ereditarietà e sub-classing


Inferenza di tipo
```ocaml
let rec map f l = match l with 
	h::l1 -> f h::map f l1 
	| _ -> [];;
```
1. `[]` è una funzione zeraria 
2. `h::l1` coinvolge l'operatore binario `::` : a x a List -> a List, quindi `h` e `l1` sono List dello stesso tipo a
3. `f` ha come tipo in input a ma come output non possiamo dire niente, b
4. QUINDI alla seconda occorrenza di `::` dovrebbe essere una List di tipo b 
5. QUINDI `map f l1` dovrebbe  avere come tipo b List
6. questo è possibile solo se il tipo di `map` è `(a -> b) x a List -> b List`