Funzione di massa di probabilità di una variabile aleatoria $X$ con supporto $D$
È una funzione con dominio i numeri reali e codominio i reali tra 0 e 1 inclusi che associa ad ogni numero reale la probabilita che la variabile aleatoria assuma tale valore
$f_X : R --> [0, 1]$
$$f_X(x) = P(X = x)$$

Proprietà che una funzione deve rispettare per essere una funzione di massa di una qualche variabile aleatoria
1. $\forall x \in R, f_X(x) \geq 0$
2. $\sum_{x_i \in D} f_X(x_i)=1$

Tracciando il grafico di questa funzione $f_X$ come a bastoncini

F risulta una funzione a gradini, F è costante su ciascuno degli intervalli $[x_{i-1}, x_i)$ e in $x_i$ fa un salto di ampiezza $f(x_i)$ passando da $f(x_1) + …+ f(x_{i-1})$ a $f(x_1) + … + f(x_{i-1}) + f(x_i)$

Funzione di ripartizione $F_X$ di una variabile aleatoria $X$ (funzione di distribuzione cumulativa) è una funzione con dominio i numeri reali e codominio i reali compresi tra 0 e 1, associa ad ogni reale la probabilita che la variabile aleatoria x assuma valori minori o uguali di tale valore
$F_X : R --> [0, 1]$
$$F_X(x) = P(X \geq x) = \sum_{x_i\leq x} f_X(x_i)$$

Ora consideriamo $F_X$ costante a tratti
Se trova una forma analitica per la funzione di ripartizione riesco a calcolare la probabilità di ogni evento $x$
$\{X \leq b\} = \{X \leq a\} \cup \{a < X \leq b\}$
$P(X \leq b) = P(\{X \leq a\}) + P(\{a < X \leq b\})$
$F_X(b) = F_X(a) + P(\{a < X \leq b\})$
$P(\{a < X \leq b\}) = F_X(b) - F_X(a)$

Tutti gli eventi più complicati li posso scindere come unione di eventi di questo tipo
Data una funzione di ripartizione quale proprietà deve essere avere
1. $\forall x \in R, F_X(x)\geq 0$
2. $\lim_{x->\infty}F_X(x)=1$
3. Deve essere continua da destra

La differenza di due salti è la differenza tra le probabilità