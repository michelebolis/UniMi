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
Parallelismo

La base di ogni computazione è il processo
Erlang adotta un modello attore per la concorrenza con 
- scambio di messaggi asincrono (ogni attore ha una coda di messaggi)
- assenza della condivisione di memoria 

Erlang è un linguaggio funzionale dinamicamente typato
Erlang supporta distribuzione, fault tolerance e hot-swapping

Sintassi base

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

```cmd
erl // entro nella Eshell
c(fact) // compilazione del modulo fact e importazione nell'interprete
fact:fact(7) // utilizzo della funzione fact del modulo fact
```

Numeri interi e float sono illimitati
Numeri formati
- k. Con k intero
- k#base con k intero e base la base in cui è k, trasforma k in base 10
- $char con char un carattere restituisce il codice ascii corrispondente
- notazione scientifica

es
```cmd
10. -> 10
16#FF. -> 255
$A. -> 65
-12.35e-2. -> -0.1235
```

Un atomo è un etichetta con iniziale minuscola che puo contenere qualcosa
Per avere un atomo con lettera maiuscola servono le '...'


Strutture dati
- Tupla

```erlang
{}. %tupla vuota
{123, "walter", cazzola}. %tupla con cazzola un atomo
```

Possono subire un pattern matching strutturale
```erlang
{{1, 2}, 3} == {1, {2, 3}}. %false perche non hanno la stessa struttura
```

Non posso aggiungere elementi: numero fissato di oggetti

- Lista 
```erlang
[]. %lista vuota
[1 | [2]]. %lista [1, 2]
length([{1, 2}, ok, []]). %3
A = [$a, $b], B = [$b, $c].
A ++ "" ++ B. % ++ operatore di concatenazione tra liste. Ris: "abbc"
A -- B. % -- operatore di sottrazione tra liste. Ris: "ac"
```

Assegnamenti
Le variabili invece hanno la lettera maiuscola, in realta sono degli alias ai valori che gli assegniamo
ATT i valori assegnati NON possono essere modificati

```erlang
A = 1. 
A = 2. %A NON è una variabile ma un nome/alias per 1
```

= non fa una selezione ma un pattern matching

```erlang
[B | L] = [a, b, c].
{X, X} = {B, B}. % Ris: {a, a}
{A1, _, [B1|_], {B1}} = {abc, 23, [22,x], {22}}.
```

B sarà la testa della lista mentre L sarà il resto della lista
Quello che non considero nel pattern matching lo rappresenterò con \_

Usate per conservare un numero variabile di oggetti, infatti hanno una dimensione dinamica

Funzione
```erlang
nomeFunzione(pattern_1, ..., pattern_k) when guardia_1 -> body_1 ;
nomeFunzione(pattern_1, ..., pattern_k) when guardia_2 -> body_2 .
```

Le clausole sono scannerizzate sequenzialmente finche non viene trovato un match

es
```erlang
-module(ex_module). 
-export([double/1]). % rendiamo disponibile SOLO double/1 e non double/2

double(X) -> double(X, 2);
double(X, N) -> X * N.
```

La guardia puo essere
- atomo
- operazioni aritmetiche/booleane
- andalso/orelse
- permitted BIFs

Map, Filter e Reduce
Disponibili nel modulo lists

```erlang
-module(mfr). 
-export([map/2,filter/2,reduce/2]). 
map(_, []) -> []; 
map(F, [H|TL]) -> [F(H)|map(F,TL)]. 

filter(_, []) -> []; 
filter(P, [H|TL]) -> filter(P(H), P, H, TL). 
filter(true, P, H, L) -> [H|filter(P, L)]; 
filter(false, P, _, L) -> filter(P, L). 

reduce(F, [H|TL]) -> reduce(F, H, TL). 
reduce(_, Q, []) -> Q; 
reduce(F, Q, [H|TL]) -> reduce(F, F(Q,H), TL).
```

Es utilizzo
```cmd
mfr:map(fun(X) -> X*X end, [1,2,3,4,5,6,7]).
mfr:filter(fun(X) -> (X rem 2)==0 end, [1,2,3,4,5,6,7]).
mfr:reduce(fun(X,Y) -> X+Y end, [1,2,3,4,5,6,7]).
```

List comprehension 
Forma generale: \[X || Qualifier1, ..., Qualifiern]
I Qualifier sono generatori o filtri booleani

es quicksort
```erlang
-module(sort). 
-export([qsort/2]). 
qsort(_, []) -> []; 
qsort(P, [Pivot|TL]) -> 
	qsort(P, [X||X<-TL, P(X,Pivot)]) ++ [Pivot] ++ qsort(P, [X||X<-TL, not P(X,Pivot)]).
	% 1a List comprehension: in X ci sono tutti gli elementi di TL che rispettano il predicato P. 
	% 2a List comprehension: in X ci sono tutti gli elementi di TL che NON rispettano il predicato P.
```

Es utilizzo
```cmd
sort:qsort(fun(X, Y) -> X<Y end, [13, 1, -1, 8, 9, 0, 3.14]). // ordine crescente
sort:qsort(fun(X, Y) -> X>Y end, [13, 1, -1, 8, 9, 0, 3.14]). // ordine decrescente
```

es genera numeri primi minori di N
```erlang
-module(prime). 
-export([primes/1]). 
primes(N) when N>1 -> 
	[X|| X <- lists:seq(2,N), 
		(length([Y || Y <- lists:seq(2, trunc(math:sqrt(X))), ((X rem Y) == 0)]
		) == 0)
	]; 
primes(_) -> [].
% Metto in X i numeri generati da 2 a N t.c. la lunghezza della lista Y sia 0.
% La lista Y, fissato un elemento di X, contiene i numeri generati da 2 alla radice di X trocata, t.c. il resto tra X e Y sia 0.
```


---

Actor Model Concurrency
I thread sono il modo tipico per ottenere la concorrenza.
L'esecuzione del programma è diviso in task concorrenti, operando su memoria condivisa

Problemi:
- update loss
- deadlock

Erlang utilizza un approccio in cui
- Ogni oggetto è un attore che ha una mailbox e un comportamento
- Gli attori comunicano tramite messaggi bufferizzati nella mailbox

La computazione è data-driven in quanto appena l'attore riceve un messaggio
- puo mandare un numero di messaggi ad altri attori
- puo creare un numero di attore
- puo assume un comportamento diverso per il prossimo messaggio nella sua mailbox

Ogni attore è caratterizzato da un indirizzo che lo identifica e da una mailbox.
I messaggi sono ordinati secondo il tempo di arrivo

Nota
- tutta la comunicazione è asincrona in quanto il mittente non aspetta che il ricevente confermi di aver ricevuto il messaggio e non viene garantito l'ordine di arrivo
- NON c è stato condiviso tra gli attori
- gli attori lavorano in modo concorrente e sono implementati come user-space threads (thread all'interno della VM di Erlang)

...

Overview della concorrenza in Erlang
I 3 elementi base della concorrenza sono
- Spawn
Funzione spawn() per creare un nuovo attore

```erlang
-module(processes_demo). 
-export([start/2, loop/2]). 
start(N,A) -> spawn (processes_demo, loop, [N,A]). 
% spawn(nomeModulo, funzione, parametriFunzione)

loop(0,A) -> io:format("~p(~p) ~p~n", [A, self(), stops]); 
loop(N,A) -> io:format("~p(~p) ~p~n", [A, self(), N]), loop(N-1,A).
% funzione self() ritorna il PID del processo
```

- Sending message
Per mandare un messaggio l'attore deve
- Sapere l'indirizzo PID del target (non posso usarlo esplicitamente)
- Mandare il proprio PID al target con il messaggio SE una risposta è necessaria
- usare !
L'operatore Exp1 ! Exp2 si usa per mandare messaggi ad altri attori
- Exp1 deve identificare un attore
- Exp2 è ogni espressione di Erlang valida; il risultato del send expressione is  one of Exp2

Nota
- L'invio non fallisce MAI anche se il target non esiste o non è raggiungibile
- L'invio non è bloccante per il mittente
- PID <0.numeroAttore.infoAggiuntive> il primo numero nel PID è l'id del nodo Erlang (es PC virtuale)

- Receiving message
Meccanismo di pattern matching dei messaggi dalla mailbox
L'attore prende dalla mailbox il messaggio piu vecchio. 
- SE la mailbox è vuota, allora è bloccato e aspetta
- SE il pattern matching fallisce, si blocca aspettando un messaggio (nessuna eccezione)

```erlang
receive 
	Pattern1 [when GuardSeq1 ] -> Body1 ; 
	... 
	Patternn [when GuardSeqn ] -> Bodyn 
	[after Exprt -> Bodyt ] 
end
```

Per evitare un attesa infinita, la clausola after è usata in modo che dopo Exprt l'attore si svegli. Solitamente si usa solo in debugging o alternativamente si mette Any -> stampaMessaggio. SE non fa pattern matching, viene lasciato nella coda aspettando altri messaggi

es 
```erlang
-module(converter). 
-export([t_converter/0]). 
t_converter() -> 
	receive 
		{toF, C} -> io:format("~p `°`C is ~p `°`F~n", [C, 32+C*9/5]), t_converter();
		{toC, F} -> io:format("~p `°`F is ~p `°`C~n", [F, (F-32)*5/9]), t_converter();
		{stop} -> io:format("Stopping`!`~n"); 
		Other -> io:format("Unknown: ~p~n", [Other]), t_converter() 
	end.
```

```cmd
Pid = spawn(converter, t_converter, []). 
Pid ! {toC, 32}.
Pid ! {stop}. 
Pid ! {toF, 100}. // quando un attore è stoppato, i messaggi vengono ignorati
```

Actor scheduling
Gli attori NON sono processi e quindi NON sono toccati dal SO
Il BEAM usa uno scheduling preemtive: quando un attore lavora per troppo tempo o quando entra in uno stato di receive e non ci sono messaggi, l'attore è fermato e viene messo nella coda di scheduling

I processi del OS e gli attori hanno diversi scheduling
Il BEAM supporta il multiprocessing simmetrico cioè puo eseguire processi in parallelo su piu CPU MA non puo eseguire attori in parallelo su piu CPU

Timing the Spawning Process

```erlang
-module(processes). 
-export([max/1]). 
max(N) -> 
	Max = erlang:system_info(process_limit), 
	io:format("Maximum allowed processes:~p~n",[Max]), 
	statistics(runtime), statistics(wall_clock), 
	L = for(1, N, fun() -> spawn(fun() -> wait() end) end), 
	{_, Time1} = statistics(runtime), 
	{_, Time2} = statistics(wall_clock), 
	lists:foreach(fun(Pid) -> Pid ! die end, L), 
	U1 = Time1 * 1000 / N, U2 = Time2 * 1000 / N, 
	io:format("Process spawn time = ~p (~p) microseconds~n", [U1, U2]). 
wait() -> receive die -> void end. 
for(N, N, F) -> [F()]; 
for(I, N, F) -> [F()|for(I+1, N, F)].
```

Dare un nome agli attori
Erlang permette con la registrazione di un attore di rendere il suo PID pubblico agli altri processi
Una volta registrato è possibile mandare un messaggio in modo diretto: name ! messaggio
Errore SE registro un attore con un atomo gia registrato 

es
```erlang
-module(clock). 
-export([start/2, stop/0]). 
start(Time, Fun) -> register(clock, spawn(fun() -> tick(Time, Fun) end)). 
					% register(atomo, PID)
stop() -> clock ! stop. 
tick(Time, Fun) -> 
	receive 
		stop -> void 
	after 
		Time -> Fun(), tick(Time, Fun) 
	end.
```

---

Error in concurrency
Quando i due attori sono collegati, gli errori di uno affetta il comportamento dell'altro

`link(PID)` function aiuta a monitorare un attore attraverso lo scambio di messaggio
SE A è linkato a B, quando B muori, viene mandato un messaggio di uscita `{'EXIT', PID}`
SE abbiamo piu processi linkati, abbiamo un link set

I segnali di uscita sono generati da un processo che muore e sono mandati in broadcast a tutti i processi linkati
Il segnale di uscita può essere esplicitato con `exit(PID, X)`

es
```Erlang
-module(dies). 
-export([on_exit/2]). 
on_exit(Pid, Fun) -> 
	spawn(fun() -> 
		process_flag(trap_exit, true), 
		link(Pid), 
		receive {'EXIT', Pid, Why} -> Fun(Why) end 
	end).
```

```cmd
Pid = spawn(fun() -> receive X -> list_to_atom(X) end end).
dies:on_exit(Pid, fun(Why) -> io:format("~p died with:~p~n",[Pid, Why]) end).
```

`process_flag(trap.exit, true)`
Permette di flaggare il processo come di sistema, consentendolo di non morire quando riceve l'exit del processo a cui è linkato

| **`trap_exit`** | **Exit signal** | **Action**                                |
| ----------- | ----------- | ------------------------------------- |
| true        | kill        | muore e propaga                       |
| true        | qualsiasi   | aggiunge {'EXIT, PID, X'} ai messaggi |
| false       | normal      | continua (NO propagazione)            |
| false       | kill        | muore e propaga                       |
| false            | qualsiasi            | muore e propaga                                      |

Situazioni:
- NON mi interessa se un processo crasha
```Erlang
PID = spawn(fun() -> ... end).
```
- Voglio che l'errore si propaghi
```Erlang
PID = spawn_link(fun() -> ... end).
```
- Voglio gestire l'errore
```Erlang
process_flag(trap_exits, true).
PID = spawn_link(fun() -> ... end).
```

es
```Erlang
-module(edemo1). 
-export([start/2]). 
start(Bool, M) -> 
	A = spawn(fun() -> a() end), 
	B = spawn(fun() -> b(A, Bool) end), 
	C = spawn(fun() -> c(B, M) end), 
	sleep(1000), status(b, B), status(c, C). 
a() -> process_flag(trap_exit, true), wait(a). 
b(A, Bool) -> process_flag(trap_exit, Bool), link(A), wait(b). 
c(B, M) -> link(B), 
	case M of 
		{die, Reason} -> exit(Reason); 
		{divide, N} -> 1/N, wait(c); 
		normal -> true 
	end.
wait(Prog) -> 
	receive 
		Any -> io:format("Process ~p received ~p~n", [Prog, Any]),
		wait(Prog) 
	end. 
sleep(T) -> 
	receive after T -> true end. 
status(Name, Pid) -> 
	case erlang:is_process_alive(Pid) of 
		true -> io:format("process ~p (~p) is alive~n", [Name, Pid]); 
		false -> io:format("process ~p (~p) is dead~n", [Name, Pid]) 
	end.
```

A processo di sistema linkato a B, B processo di sistema SE Bool è True e C muore con ragione M

- Quando C muore in modo normale, B non muore e quindi neanche A
```cmd
edemo1:start(false, {die, normal}).
```
- B non essendo di sistema, quando C muore per una ragione non normale, allora anche B muore MA A rimane viva perché è di sistema
```cmd
edemo1:start(false, {die, abc}).
```
- B non essendo di sistema, quando C muore per `{badarith, ...}` muore anche lui propagando a A
```cmd
edemo1:start(false, {divide, 0}).
```
- B essendo di sistema, cattura l'errore che non verrà propagato ad A
```cmd
edemo1:start(true, {divide, 0}).
```

Nota
`erlang:is_process_alive(Pid)` SE il processo è vivo, True ALTRIMENTI False


Monitor
I link sono simmetrici; per ottenere link asimmetrici si utilizzano i monitor
SE A monitora B, quando B muore A riceverà un segnale di uscita MA SE A muore, B non riceverà un segnale

Creazione di un monitor per un processo A su un B: `erlang:monitor(process, B)`
Quando B muore con segnale di uscita Reason, `{'Down', Ref, process, B, Reason}` viene mandato a A, con Ref il riferimento al monitor

---

Distribution in Erlang
Stesso servizio replicato su piu macchine/VM
Vantaggi
- Performance: grazie all'esecuzione parallela
- Affidabilità: per distribuire la fault tollerance
- Scalabilità: aggiungendo un altra macchina, duplico le risorse
- Applicazione intrinsecamente distribuite: es chat, multi-user game

2 modelli
- Distributed Erlang
Si basa sul concetto di Erlang nodes, singola VM che comunica con altra VM in esecuzione sullo stesso pc o su altri

es
```Erlang
-module(kvs). 
-export([start/0, store/2, lookup/1]). 
start() -> register(kvs, spawn(fun() -> loop() end)). 
store(Key, Value) -> rpc({store, Key, Value}). 
lookup(Key) -> rpc({lookup, Key}). 
rpc(Q) -> 
	kvs ! {self(), Q}, 
	receive 
		{kvs, Reply} -> Reply 
	end. 
loop() -> 
	receive 
		{From, {store, Key, Value}} -> 
			put(Key, {ok, Value}), From ! {kvs, true}, loop(); 
		{From, {lookup, Key}} -> From ! {kvs, get(Key)}, loop() 
	end.
```

```cmd1
erl -sname server
kvs:start().
kvs:lookup(weather).
```

```cmd2
erl -sname client
rpc:call(server@surtur, kvs, store, [weather, sunny]).
rpc:call(sif@surtur, kvs, lookup, [weather]).
```

`erl -sname nomeTerminale`: permette di avere un terminale server con un nome specifico che poi richiamerò da un altro terminale client
`rpc:call` libreria standard
I cookie si utilizzano per comunicazione ssh

Erlang Node è una VM Erlang con il proprio indirizzo e set di processi
SE abbiamo tanti nodi, abbiamo un cluster
Le primitive nei sistemi distribuiti, hanno un argomento in piu, cioè il Node
- `spawn(Node, Mod, Func, ArgList)-> Pid`
- `spawn_link(Node, Mod, Func, ArgList)-> Pid`
- `disconnect_node(Node) -> bools() | ignored`
- `monitor_node(Node, Flag) -> true`
- `{RegName, Node} ! Msg`

es
```Erlang
-module(ddemo). 
-export([rpc/4, start/1]). 
start(Node) -> spawn(Node, fun() -> loop() end). 
rpc(Pid, M, F, A) -> 
	Pid ! {rpc, self(), M, F, A}, 
	receive {Pid, Response} -> Response end. 
loop() -> 
	receive 
		{rpc, Pid, M, F, A} -> 
			Pid ! {self(), (catch apply(M, F, A))},
			loop() 
	end.
```

apply(M, F, A) permette di eseguire la funzione F del modulo M con parametri A
guardare in libreria rpc e global

due Node per comunicare devo avere lo stesso cookie
erl -setcookie "Cookie"
erlang:set_cookie(node(), "Cookie")
Problema: posso eseguire qualsiasi cosa


- Socket-Based Distribution
Controllo piu granulare, posso decidere quali processo posso fare cosa...

si usa libreria lib_chan, un modulo che permette di esplicitare quale processo possono essere spawati 

notUsed per specificare nel file di config che la funzione non prende argomenti

lib_chan non lo chiede all esame

---

IRC lite
