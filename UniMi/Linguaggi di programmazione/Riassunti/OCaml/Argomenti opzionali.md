```ocaml
let arg x = func y rest -> rest (op x y)
let stop x = x
let f g = g init

(* es *)
let op = fun x y -> x+y
let init = 0
f (arg 1) (arg 2) stop (* = 3*)
``` 