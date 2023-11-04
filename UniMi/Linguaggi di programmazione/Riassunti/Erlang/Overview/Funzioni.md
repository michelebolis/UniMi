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

[[Map, Filter e Reduce]]