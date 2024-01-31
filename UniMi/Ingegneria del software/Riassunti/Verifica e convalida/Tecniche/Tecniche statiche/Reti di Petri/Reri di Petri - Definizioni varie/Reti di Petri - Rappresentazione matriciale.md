E' possibile rappresentare/definire una rete di Petri mediante delle matrici
Definiamo 3 matrici
- $I$ la matrice degli archi di input alle transizioni
- $O$ la matrice degli archi di output alle transizioni

$p: 1..|P| -> P$ è una funzione che assegna un indice ad ogni posto
$t:1..|T| -> T$ è una funzione che assegna un indice ad ogni transizione

Le due matrici $I$ e $O$ sono $|P| \text{ } X \text{ } |T|$
$\forall <p(i), t(j)> \in F, I[i][j] = W(<p(i), t(j)>)$
$\forall <p(i), t(j)> \notin F, I[i][j] = 0$
$\forall <t(j), p(i)> \in F, O[i][j] = W(<t(j), p(i)>)$
$\forall <t(j), p(i)> \notin F, O[i][j] = 0$

Notazione $X[.][k]$ è il vettore colonna $k$ di una matrice $X$

- $M$ la matrice della marcatura dei posti

Un vettore colonna $m$ di dimensione |P| rappresenta la marcatura M
$\forall i \in 1..|P|, m[i] =M(p(i))$

La transizione $t_j$ è abilitata in una marcatura espressa dal vettore $m$
$m[t_j >$ SE e SOLO SE $I[.][j] \leq m$

Lo scatto di una transizione $t_j$ in una marcatura $m$ produce la marcatura $m'$
$m[t_j > m'$ con $m' = m-I[.][j]+O[.][j]$

[[Reti di Petri - Matrice di incidenza]]
[[Retri di Petri - Rappresentazione matriciale Esempio]]
