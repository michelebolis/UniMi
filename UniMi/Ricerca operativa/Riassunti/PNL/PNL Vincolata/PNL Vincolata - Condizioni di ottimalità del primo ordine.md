Definita la funzione Lagrangiana
$$L(x, \lambda) = f(x)-\sum_{i \in E \cup I}\lambda_ic_i(x)$$
si hanno le seguenti `condizioni necessarie del primo ordine` affinché un punto sia un minimo locale
Condizioni di `Karusk-Kuhn-Tucker` `KKT` SE
- $x^*$ è un minimo locale di $f(x)$
- $f(x)$ e $c_i(x)$ sono funzioni continue e differenziabili
- la LICQ è soddisfatta in $x^*$

ALLORA esiste un $\lambda^*$ t.c.
$$\bigtriangledown_x L(x^*, \lambda^*)=0$$
$$\begin{cases} 
c_i(x^*)=0, \forall i \in E \\
c_i(x^*) \geq 0, \forall i \in I \\
\lambda_i^* \geq  0, \forall i \in I \\
\lambda_i^*c_i(x^*) = 0, \forall i \in E \cup I
\end{cases}$$
Spiegazione
$$\begin{cases} \text{ammissibilita dei vincoli di uguaglianza} \\ 
\text{ammissibilita vincoli di disuguaglianza} \\
\text{moltiplicatori non negativi quando corrispondo a vincoli di disuguaglianza} \\
\text{condizione di complementarieta (reminder a scarto complementare)} 
\end{cases}$$

Le `condizioni di complementarietà`
$$\lambda_i^*c_i(x^*) = 0, \forall i \in E \cup I$$
richiedono che 
- o il vincolo $c_i(x)$ sia attivo
- o il corrispondente moltiplicatore $\lambda_i$ sia nullo
- o entrambe 

Poiché $\lambda_i^*=0, \forall i \notin A(x^*)$, la condizione del primo ordine si puo riscrivere come 
$$\bigtriangledown f(x^*)-\sum_{i \in A(x^*)}\lambda_i^*\bigtriangledown c_i (x^*)=0$$
Si ha `complementarietà stretta` quando solo una tra $\lambda_i^*$ e $c_i(x^*)$ è nulla $\forall i \in A(x^*)$
Per uno stesso punto $x^*$ potrebbero esistere diversi $\lambda_i^*$ che soddisfano le condizioni KKT MA `se valgono le condizioni LICQ`, ALLORA $\lambda_i^*$ è `unico`