Le tuple sono [[liste]] con una dimensione fissata e sono $eterogeneee$

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
