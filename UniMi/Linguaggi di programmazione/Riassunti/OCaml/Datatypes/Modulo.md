Il modulo è un modo per specificare un nostro tipo di dato in OCaml con le relative funzioni e operazioni
Parti: 
- Interfaccia pubblica che espone solo le funzioni e i tipi specificati che vogliamo siano visibili e utilizzabili dall'utente
- Modulo implementativo

 ```ocaml
 module A : 
	sig
		(* Interfaccia *)
		(* es *)
		type char_queue (* now abstract *) 
		val empty : char_queue 
		val insert : char_queue -> int -> char -> char_queue 
		val extract : char_queue -> int * char * char_queue 
		exception QueueIsEmpty
	end =
	struct
	(* Implementazione *)
	end;;
  ```

$as$ per renaming

L'interfaccia mi permette di opacizzare il tipo e nascondere le operazioni che non devono essere visibili dall'esterno 

ATT i moduli devono avere la lettera maiuscola 

Per aprire un modulo: open nomeModulo.nomeModulo;;

Functors
Funtore è una funzione da struttura a struttura. Permette di avere una segnatura fissata di un input e output potendo così modificare dettagli implementativi senza intaccare nessun modulo che utilizza
Vantaggi:
- Evitare duplicazione (Generalizziamo sul dato)
- Incrementare ortogonalità

Funtore istanzia due algoritmi diversi

Funtore es

 ```ocaml
let is_balanced str = let s = Stack.empty in try 
	String.iter 
		(fun c -> match c with 
			'(' -> Stack.push s c 
		  | ')' -> Stack.pop s 
		  | _ -> ()) str; 
		Stack.is_empty s 
	with Stack.EmptyStackException -> false

module type StackADT = 
	sig 
		type char_stack 
		exception EmptyStackException 
		val empty : char_stack 
		val push : char_stack -> char -> unit 
		val top : char_stack -> char 
		val pop : char_stack -> unit 
		val is_empty : char_stack -> bool
	end

module Matcher (Stack : StackADT.StackADT) = 
	struct 
		let is_balanced str = 
			let s = Stack.empty in try 
				String.iter 
					(fun c -> match c with 
						'(' -> Stack.push s c 
					  | ')' -> Stack.pop s 
					  | _ -> ()) str; 
				Stack.is_empty s 
			with Stack.EmptyStackException -> false 
	end
 ```

In questo caso $Matcher$ è un funtore che lega il nostro algoritmo alla struttura astratta Stack

 ```ocaml
module BoundedStack = struct 
	type char_stack = { 
		mutable c: char array; 
		mutable top: int } 
	exception EmptyStackException 
	let empty = {top=0; c=Array.make 10 ' '} 
	let push s x = 
		s.c.(s.top) <- x; 
		s.top <- s.top+1 
	let pop s = 
		match s.top with 
			0 -> raise EmptyStackException 
		  | _ -> s.top <- s.top -1 
	let top s = 
		match s.top with 
			0 -> raise EmptyStackException 
		  | _ -> s.c.(s.top) 
	let is_empty s = (s.top = 0) 
end;;
 ```

L'implementazione $BoundedStack$ è aderente all'interfaccia $StackADT$ 

 ```ocaml
 module M0 = Matcher(BoundedStack);;
  ```
