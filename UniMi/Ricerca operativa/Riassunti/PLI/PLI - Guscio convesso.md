Dato un insieme discreto X, il suo guscio convesso è il poliedro
$$X = \{x_1,  ..., x_t\}, x_i \in R^n,  \forall i=1,..., t$$
$conv(X) = \{x \in R^n : x = \sum_{i=1}^t \lambda_i x_i, \sum_{i=1}^t \lambda _i = 1, \lambda _i \geq 0, \forall i =1,...,t\}$
E' un poliedro i cui punti estremi sono elementi dell'insieme discreto X
Data una formulazione P e l'insieme discreto X delle sue soluzioni ammissibili vale
$$X \subseteq conv(X) \subseteq P$$
In generale non conosciamo la formulazione ideale dei problemi di ottimizzazione lineare discreta (es problema del cammino minimo su grafo...)
Il numero dei vincoli del guscio convesso puo crescere esponenzialmente con la dimensione dell'istanza

Conosciamo la formulazione ideale solo per alcuni problemi di ottimizzazione discreta
La disciplina che studia tale questione è la polyhedral combinatorics
