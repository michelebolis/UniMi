#ML è un linguaggio di programmazione funzionale general purpose sviluppato negli anni 70
Features:
- first-class functions, parametric polymorphism
- Fortemente typato ma posso in realta anche ometterli, pattern matching, exception handling

==OCaml è un'implementazione di ML==
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
MA -1 non è una costante, ma una funzione seguita da 1 QUINDI sto dando a $succ$ come argomento una funzione $int -> int$, l operazione -

==Un nuovo binding (riuso di un nome) nasconde la prima volta che ho usato quel nome==

### Composizione di funzione
```ocaml
let compose f g x = f (g x);; 
let compose' (f, g) x = f (g x);;
 ```
Hanno tipi diversi
- ('a -> 'b) -> ('c -> 'a) -> 'c -> 'b
* ('a -> 'b) * ('c -> 'a) -> 'c -> 'b
	L'argomento richiesto rappresenta la $tupla$, le parentesi sono fonte di errore

### Pattern matching
I costrutti If non si usano, vengono usati i pattern matching per definire funzioni
```ocaml
match expression with 
	| pattern when boolean expression -> expression 
	| pattern when boolean expression -> expression
 ```

Catchall si dovrebbe sempre mettere con un \_ , in modo da catturare i casi non previsti nei pattern
