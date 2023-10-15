ML è un linguaggio di programmazione fortemente e staticamente typato, MA i tipi sono inferito dall'uso che fai degli operatori.

es
 ```ocaml
let pi = 4.0 * atan 1.0
(* Error: This expression has type float but an expression was expected of type int *)
 ```
Il sistema di inferenza prevede che * sia solo per interi, non c è una conversione implicita , quindi dovrò usare $*.$ che è un operazione per i float

Tipi primitivi
- #Boolean
	Costanti:
	- `true`
	- `false`
	Operatori 
	- `&&`, `||`, `not`
	- `==`, `<>`

- #Stringhe
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

[[Collezioni]]
[[Modulo]]
[[Polimorfismo]]