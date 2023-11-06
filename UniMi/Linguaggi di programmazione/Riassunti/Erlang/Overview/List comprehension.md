Forma generale: \[X || Qualifier1, ..., Qualifiern]
I Qualifier sono generatori o filtri booleani

es quicksort
```erlang
-module(sort). 
-export([qsort/2]). 
qsort(_, []) -> []; 
qsort(P, [Pivot|TL]) -> 
	qsort(P, [X||X<-TL, P(X,Pivot)]) ++ [Pivot] ++ qsort(P, [X||X<-TL, not P(X,Pivot)]).
	% 1a List comprehension: in X ci sono tutti gli elementi di TL che rispettano il predicato P. 
	% 2a List comprehension: in X ci sono tutti gli elementi di TL che NON rispettano il predicato P.
```

Es utilizzo
```cmd
sort:qsort(fun(X, Y) -> X<Y end, [13, 1, -1, 8, 9, 0, 3.14]). // ordine crescente
sort:qsort(fun(X, Y) -> X>Y end, [13, 1, -1, 8, 9, 0, 3.14]). // ordine decrescente
```

es genera numeri primi minori di N
```erlang
-module(prime). 
-export([primes/1]). 
primes(N) when N>1 -> 
	[X|| X <- lists:seq(2,N), 
		(length([Y || Y <- lists:seq(2, trunc(math:sqrt(X))), ((X rem Y) == 0)]
		) == 0)
	]; 
primes(_) -> [].
% Metto in X i numeri generati da 2 a N t.c. la lunghezza della lista Y sia 0.
% La lista Y, fissato un elemento di X, contiene i numeri generati da 2 alla radice di X trocata, t.c. il resto tra X e Y sia 0.
```
