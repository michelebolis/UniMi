A differenza di quando usiamo un algoritmo di separazione euristico, con i tagli di Gomory si riesce sempre ad andare avanti. Usano la procedura di [[PLI - Procedura di Chvatal-Gomory]]

Data una soluzione frazionaria $x^*$ del rilassamento continuo di un problema di PLI, si utilizza la procedura di Chvatal-Gomory sul vincolo associato a una variabile frazionaria in modo da ottenere una disuguaglianza valida violata da $x^*$

Dato un problema P di PLI e il suo rilassamento continuo LP
$$P) max\{cx : ax = b, x\geq 0, x \in Z^n\}$$
$$LP) max\{cx : ax = b, x\geq 0\}$$
siano $x^*$ e $z^*$ la sua soluzione ottima di LP e il suo valore 
$z^* = \overline{a}_{00} + \sum_{j \in NB^*}{\overline{a}_{0j}x_j^*}$
$$\begin{cases} x^*_{B*i} + \sum _{j \in NB^*}{\overline{a}_{ij} x^*_j = \overline{a}_{i0}, \forall i = 1,...,m} \\ x^* \geq 0 \end{cases}$$

La soluzione ottima sappiamo che è la somma di una costante (in alto a sinistra nel tableau) e dalla somma delle colonne fuori base (NB) dei coefficienti che leggo sulla riga 0 del tableau moltiplicate per le $x^*_j$
variabili in base piu la somma delle altre deve dare il termine nodo della riga

SE $x^*$ non è intero, esiste almeno un involo $\hat{i}$ t.c. $\overline{a}_{\hat{i}0}$ non è intero
Eseguendo la procedura di Chvatal-Gomory su di esso si ottiene
$$x_{B*\hat{i}} + \sum _{j \in NB^*}{\lfloor\overline{a}_{\hat{i}j} \rfloor x_j} \leq \lfloor\overline{a}_{\hat{i}0}\rfloor$$
Sottraendo questa disuguaglianza dal vincolo di uguaglianza (riportata di seguito)
$$x^*_{B*\hat{i}} + \sum _{j \in NB^*}{\overline{a}_{\hat{i}j} x^*_j} = \overline{a}_{\hat{i}0}$$
Si ottiene il taglio di Gomory
$$\sum _{j \in NB^*}{f_{\hat{i}j}x_j \geq f_{\hat{i}0}}$$
Dove 
- $f_{\hat{i}j} = \overline{a}_{\hat{i}j} - \lfloor \overline{a}_{\hat{i}j} \rfloor$
- $f_{\hat{i}0} = \overline{a}_{\hat{i}0} - \lfloor \overline{a}_{\hat{i}0} \rfloor$
- Anche la variabile di slack associata a questa disuguaglianza è intera

es [[PLI - Es Tagli di Gomory]]