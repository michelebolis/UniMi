Il modo piu semplice di definire un nuovo tipo, è dare un nuovo nome ad un tipo esistente
 ```ocaml
 type int_pair = int * string
 let a : int_pair = (1, "3")
  ```
In questo caso quindi `*` indica la definizione dei componenti di una tupla