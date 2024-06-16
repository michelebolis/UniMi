Variabili binarie
Molto spesso le variabili nei problemi di ottimizzazione rappresentano quantita che possono essere sia continue che discrete

- Le variabili binarie rappresentano `scelte logiche` con un dominio {0, 1}
Cioe quando
- non hanno un'unita di misura 
- non ammettono approssimazioni

Le variabili binarie hanno un enorme importanza dal punto di vista modellistico
$x_i = 1$ SE capita l'evento $i$
$x_i = 0$ SE NON capita l'evento $i$

- Le relazioni tra variabili binarie esprimono condizioni logiche

| Condizione                   | Significato                                               |
| ---------------------------- | --------------------------------------------------------- |
| $\sum_{i=1}^{N}{x_i} \leq 1$ | Non deve capitare piu di uno tra N eventi                 |
| $\sum_{i=1}^{N}{x_i} = 1$    | Deve capitare uno tra N possibili eventi                  |
| $\sum_{i=1}^{N}{x_i} \geq 1$ | Deve capitare almeno uno di N possibili eventi            |
| $x_1=x_2$                    | I due eventi devono capitare entrambi o nessuno dei due   |
| $x_1 \leq x_2$               | L'evento 1 puo verificarsi solo se si verifica l'evento 2 |
- Le variabili binarie sono usate per selezionare sotto insiemi di un insieme
$$\sum_{i=1}^{N}{c_ix_i} \Leftrightarrow \sum_{i \in S}{c_i}$$
dove $S$ è un sottoinsieme di {$1, ..., N$} corrispondente al vettore $x$
$$x_i = \begin{cases} 1, i \in S \\ 0, i \notin S \end{cases}$$
Le variabili binarie sono usate per eliminare i "se" dai modelli
$$\begin{cases} 0 \leq y \leq u, \text{SE } x= 1 \\ y=0, \text{SE } x=0 \end{cases} \Leftrightarrow 0 \leq y  \leq ux$$
es costi fissi
![[Pasted image 20240327150916.png|400]]

- Le variabili binarie possono essere `usate anche per attivare e disattivare i vincoli`
Dato il vincolo, aggiungendo M abbastanza grande
$$y \leq Q + Mx$$
Qualunque sia il valore di y, in realta dopo aver aggiunto Mx il vincolo risulta soddisfatto e quindi è come se lo disattivassi
Equivale a 
$$\begin{cases} y \leq Q, \text{SE } x = 0 \\ y, \text{SE } x = 1 \end{cases}$$

es vincoli disgiunti
$$|a-b|\geq k$$
essendo $a$ e $b$ due variabili continue non negative e $k >0$
Il vincolo non è lineare ed è un vincolo disgiunto
$$|a-b|\geq k \Leftrightarrow (a-b \geq k) \text{ OR } (a-b  \leq -k)$$
Si puo linearizzare introducendo una variabile binaria $x$ ed una costante $M$ grande
$$\begin{cases} a-b\geq k - Mx \\ a-n \leq -k+M(1-x) \end{cases}$$
A seconda del valore di x, uno dei due vincoli viene imposto mentre l'altro risulta disattivato

es regioni ammissibili non convesse 
![[Pasted image 20240327151950.png|400]]

es problema dello scheduling
![[Pasted image 20240327152011.png|400]]
