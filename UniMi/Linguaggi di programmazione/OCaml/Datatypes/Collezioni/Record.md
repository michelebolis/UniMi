I record/strutture sono accessibili mediante i nomi dei campi eterogenei (ed eventualmente mutabile con la keyword `mutable`)

Sintassi:
 ```ocaml
 type record = {campo1: tipo_campo1; mutable campo2: tipo_campo2}
 let var = {campo1= "a"; campo2 = 1}
 ```

Modo per definirli:
- [[Aliasing]]
- [[Variants]]