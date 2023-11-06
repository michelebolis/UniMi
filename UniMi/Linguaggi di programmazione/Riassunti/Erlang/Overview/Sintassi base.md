
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
