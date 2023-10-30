Programmazione funzionale
Caratteristiche
- Le funzioni sono classi di primo livello: quindi invece di passare come argomento ad una funzione dei dati, posso passare un'altra funzione 
- Uso la ricorsione come struttura di controllo invece del while e del for
- Focus sul list processing o in generale dati organizzati in un insieme, sempre attraverso la ricorsione
- Dato che tutto è una funzione, QUINDI non ci sono side effects (la maggior parte dei linguaggi funzionali puri), non ha stato
Conseguenze
- Riduciamo gli errori in quanto l'errore non si puo propagare piu di troppo non essendoci stato
- E' piu facile dimostrare alcune proprietà del nostro SW in quanto dato quell'input ho SEMPRE quell'output

Obiettivo: modellare ogni cosa come una funzione matematica

Costruttori:
- Astrazione per definire la funzione
- Applicazione per chiamare la funzione
Non essendoci stato, le variabili sono solo nomi.

λ-Calculus Church and Kleene ∼1930
λ-espressioni sono fatte da costanti, variabili, λ, . e parentesi:
- SE x è una variabile o una costante, allora x è una λ expression
- SE x è una variabile e M è una λ expression, ALLORA λx.M è una λ expression
- SE M, N sono λ expression ALLORA (MN) è una λ expression

es 
- Astrazione λx.x+1
- Applicazione (λx.x+1)7

Applicazione ha priorita a sinistra
MNP = (MN)P


OCaml
ML è un linguaggio di progammazioni funzionale general purpose svillupo negli anni 70
Features:
- first-class functions, parametric polymorphism
- Fortemente typato ma posso in realta anche ometterli, pattern matching, exception handling

OCaml è un'implementazione di ML
OCaml dispone sia di un interpretatore $ocaml$ che di un compilatore $ocamlc$

 ```ocaml
let main() = print_string("Hello World in ML Style\n");; 
main();;
 ```
$let$ è la keyword per dichiarare variabili
I 2 ;; sono il comando per segnalare l'esecuzione

$unit$ indica il nulla, es il main definito sopra

```ocaml
let succ = fun x -> x+1;;
succ 2;;
 ```
Per utilizzare una funzione, uso la sua applicazione, quindi $nomeFunzione$ $argomenti$

```ocaml
let succ = fun x -> x+1;;
succ -1;;
 ```
MA -1 non è una costante, ma una funzione seguita da 1 QUINDI sto dando a succ come argomento una funzione int -> int, l operazione -

Un nuovo binding (riuso di un nome) nasconde la prima volta che ho usato quel nome

Composizione di funzione
```ocaml
let compose f g x = f (g x);; 
let compose' (f, g) x = f (g x);;
 ```
Hanno tipi diversi
- ('a -> 'b) -> ('c -> 'a) -> 'c -> 'b
* ('a -> 'b) * ('c -> 'a) -> 'c -> 'b
	L'argomento richiesto rappresenta la tupla, le parentesi sono fonte di errore

I costrutti If non si usano, vengono usati i pattern matching per definire funzioni
```ocaml
match expression with 
	| pattern when boolean expression -> expression 
	| pattern when boolean expression -> expression
 ```

Catchall si dovrebbe sempre mettere con un \_ come safe rule, in modo da catturare i casi non previsti nei pattern

Ocaml ha un pattern matching esaustivo

---

```ocaml
let invert = function
	| pattern when boolean expression -> expression 
 ```
Nasconde l ultimo argomento (in questo caso l'unico) rendendolo implicito 


## Ricorsione
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


## Datatypes 
ML è un linguaggio di programmazione fortemente e staticamente typato, MA i tipi sono inferito dall'uso che fai degli operatori.

es
 ```ocaml
let pi = 4.0 * atan 1.0
(* Error: This expression has type float but an expression was expected of type int *)
 ```
Il sistema di inferenza prevede che * sia solo per interi, non c è una conversione implicita , quindi dovrò usare $*.$ che è un operazione per i float

Tipi primitivi
- Boolean
Costanti:
- `true`
- `false`
Operatori 
- `&&`, `||`, `not`
- `==`, `<>`

- Stringhe
Le stringhe sono native in OCaml.
Ci sono diverse operazioni dal modulo `String` [(documentazione)](https://v2.ocaml.org/api/String.html)
Le stringhe sono $immutabili$ ma possono essere modificate usando Bytes/Bytes.net
Operatori:
- ^ per concatenazione delle stringhe 
- .\[] per accedere ai char, le \[] sono il nome della funzione

 ```ocaml
let s = "walter cazzola"
let b = Bytes.of_string s ;; 
(*val b : bytes = Bytes.of_string "walter cazzola" *)
Bytes.set b 0 'W'; Bytes.set b 7 'C';
(*val s : string = "Walter Cazzola"*)
 ```

## Collezioni
- Liste
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

- Tuple
Le tuple hanno una dimensione fissata e sono $eterogeneee$

Sintassi:
 ```ocaml
 let tupla = (valore1, valore2, valore3)
  ```

Le pair o coppie sono tuple con solo 2 elementi
Sintassi:
 ```ocaml
 let pair = (valore1, valore2)
 fst pair (*Restituisce valore 1*)
 snd pair (*Restituisce valore 2*)
  ```

- Array
Gli array sono liste omogenee e mutabili direttamente accessibili
Gli operatori provengono dal modulo Array [(documentazione)](https://v2.ocaml.org/api/Array.html)

Sintassi:
 ```ocaml
 let array = [|valore1;valore2;valore3|]
 let a = Array.make n x_to_initialize;;
 a.(1) <- 5 (*esempio assegnamento*)
 Array.concat [aarray; another_array]
 let a_matrix = Array.make_matrix n_row n_column x_to_initialize ;;
 a_matrix.(1).(2) <- 'z' (*esempio assegnamento*)
  ```

- Record
I record/strutture sono accessibili mediante i nomi dei campi eterogenei (ed eventualmente mutabile con la keyword `mutable`)

Sintassi:
 ```ocaml
 type record = {campo1: tipo_campo1; mutable campo2: tipo_campo2}
 let var = {campo1= "a"; campo2 = 1}
 ```

- Aliasing
Il modo piu semplice di definire un nuovo tipo, è dare un nuovo nome ad un tipo esistente
 ```ocaml
 type int_pair = int * string
 let a : int_pair = (1, "3")
  ```
In questo caso quindi `*` indica la definizione dei componenti di una tupla

- Variants
Per la definizione di un nuovo type, faccio un matching strutturale, in cui ogni caso è identificato da un nome con la prima lettera maiuscola, chiamato costruttore, eventualmente con un type specificato.

 ```ocaml
 type int_option = Nothing | AnInteger of int ;;
 let a = Nothing;; (*sarà: - : int_option = Nothing*)
 let a = AnInteger 7;; (*sarà: - : int_option = AnInteger 7*)
  ```

Sto definendo il dominio di una funzione con un pattern matching usando i costruttori

Se sto facendo piu definizioni contemporaneamente, uso l'`and`

es
 ```ocaml
 type card = Card of regular | Joker 
	 and regular = { suit : card_suit; name : card_name; } 
		 and card_suit = Heart | Club | Spade | Diamond 
		 and card_name = Ace | King | Queen | Jack | Simple of int;;
```
In questo esempio definisco `card` che o è `Card` o è `Joker`. 
`Card` sarà un record di tipo `regular` ma non avendolo definito uso l'$and$ per definirlo "inline".
La stessa cosa accade anche per `card_suit` e `card_name` che sono due tipi definiti "inline" con le Variants.

---

Modulo
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

Utilizzo del funtore

---

Polimorfismo
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

() necessarie quando una funzione non prende nessun argomento in quanto seno sarebbe naming

argomenti di default 
?nomeArgomento x

---

Currying è una tecnica per trasformare una funzione con argomenti multipli in una catena di funzioni ognuna con un singolo argomento

Applicazione parziale porta ottimizzazione
Si basa sulla posizione nella definizione

OCaml si usa named parameters 

```ocaml
 let compose ~f ~g x = f (g x) 
 let compose' = compose ~g: (fun x -> x**3.)
```

Funzioni tipiche della programmazione funzionale
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

Come usare argomenti opzionali: struttura generale per n argomenti
```ocaml
let arg x = func y rest -> rest (op x y)
let stop x = x
let f g = g init

(* es *)
let op = fun x y -> x+y
let init = 0
f (arg 1) (arg 2) stop (* = 3*)
``` 

---

Erlang
Linguaggio di programmazione orientato alla concorrenza
Le VM sono l ambiente su cui faremo girare il nostro programma

Concorrenza: processi/thread sulla stessa macchina, sono concorrenti per una risorsa, in particolare per il tempo della CPU
Parallelismo: se nelle CPU abbiamo piu core e quindi 

La base di ogni computazione è il processo
Adotta un modello attore per la concorrenza con 
- scambio di messaggi asincrono
- non c è la condivisione di memoria 

Erlang è un linguaggio funzionale dinamicamente tipato
Ogni attore ha una coda di messaggi

```erlang
- module(nomeModulo).
- export(nomeFunzione/numParametri)
``` 

```erlang
- module(fact).
- export([fact/1]).
fact(0) -> 1;
fact(N) -> N * fact(N-1).
``` 

Numeri interi e float sono illimitati

c(fact). permette di compilare e di importare nell'interprete

...

Un atomo è un etichetta con iniziale minuscola che puo contenere qualcosa
Per avere un atomo con lettera maiuscola servono le '...'

Strutture dati
- Tupla
{123, "walter", cazzola}
Possono subire un pattern matching strutturale
{{1, 2}, 3} == {1, {2, 3}}.
Non posso aggiungere elementi

- Lista 
\[1 | \[2]]

...

A = 1
A NON è una variabile ma un nome/alias per 1
A = 2

= non fa una selezione ma un pattern matching

\[B | L] = \[a, b, c]
B sarà la testa della lista mentre L sara il resto della lista

quello che non mi interessa lo rappresentero con \_


Funzione
nomeFunzione(pattern1, pattern2, ...) when guardia -> body ;
nomeFunzione(pattern1, pattern2, ...) when guardia -> body .

La guardia puo essere
- atomo
- operazioni aritmetiche/booleane
- andalso/orelse
- permitted BIFs

List comprehension 





































