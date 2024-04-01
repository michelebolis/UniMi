Dato il problema fissato mi chiedo le risorse necessarie
SE trovo algoritmo so che le risorse utilizzate sono sufficiente ma non so se sono necessarie
Sia
- $r$ una risorsa computazionale
- $\pi$ problema risolubile algoritmicamente

- Upper bound
$f: N --> N$ funzione
$f(n)$ la risorsa $r$ è sufficiente per risolvere $\pi$ SE esiste algoritmo $A$ che risolve $\pi$ utilizzando su OGNI input di lunghezza $n$, $\forall n\geq0$, al piu $f(n)$ risorsa $r$
- Lower bound
$g: N --> N$ funzione
$g(n)$ risorsa $r$ è necessaria per risolvere $\pi$ SE per ogni algoritmo $A$ che risolve $\pi$ esiste un input di lunghezza $n$, per ogni $n\geq0$, su cui $A$ utilizza almeno $g(n)$ risorsa $r$

Es
$\pi$=sort
$r$=Numero confronti

ALGORITMO insertSort $\Theta(n^2)$ --> ho un upper bound
Mi chiedo questo è anche necessario?  
Abbiamo dimostrato il lower bound di $\Theta(n*\log n)$ per sort con confronti
L'ideale sarebbe diminuire il gap tra upper e lower bound