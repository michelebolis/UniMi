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
	| pattern when boolean expression -> expression
 ```
nasconde l ultimo argomento rendendolo implicito 


ricorsione
...

 ```ocaml
let rec fact(n) = if n<=1 then 1 else n*fact(n-1)
 ```
devo dire esplicitamente che sia ricorsiva con rec

record di attivazione/frame
essendo impilati, l'argomento e il valore di ritorno sono in posizioni note, in particolare il valore di ritorno e l'argomento sono in alto e in basso

soluzione iterativa alla fine richiede sempre 3 valori

itertiva piu efficiente 

ottimizzazione possibile: memorization/caching

problema mi serve l n precedente, un dato locale, per questo mi serve un record di attivazione 
Per evitare l'verhead serve la ricorsione in coda, accumulando in un ulteriore argomento tutto

...


staticamente tipato, MA io non scrivo i tipi, i tipi sono inferito dall uso che fai degli opertori
MA il sistema di inferenza prevede che * sia solo per interi, non c è una coversione inplicita , quindi dovro usare \*. che è un operazione per i float

operatori 
...

Stringhe
^ per concatenazione delle stringhe 
.\[] per acceedere ai char, le \[] sono il nome della funzione

ATT le stringhe sono immutabili, bisogna usare Bytes.set stringa posizione char

Le liste sono omogenee
la concatenazione è inefficiente, meglio usare il costruttore in testa e poi invertier 

sul pattern matching non posso usare stringhe ma posso sulle liste perche ho un costruttore 


le tuple hanno una dimensione fissata e sono eterogeneee

pair sono tuple di 2 dimensioni
le coppie posso usare first e second


array sono omogeneo e mutabili
...

<- per assegnare

matrice


record/strutture con campi eterogenei
keyword mutable 

per i record fa un matching strutturale

sto definendo il dominio di una funzione con un pattern matching usando i costruttori

definizzioe fatte insieme usando l and




























































































