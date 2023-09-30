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

Catchall si dovrebbe sempre mettere con un \_ , in modo da catturare i casi non previsti nei pattern

