Considerando un vincolo $c(x) = 0$ ed un punto $\overline{x}$ su di esso
Indichiamo con  $\bigtriangledown c(\overline{x})$ ("nabla" c) la direzione della normale (perpendicolare) al vincolo in $\overline{x}$
Consideriamo un passo infinitesimo da $\overline{x}$ lungo una direzione $d$
Per mantenere l'ammissibilità rispetto al vincolo, $d$ deve essere t.c.
$$\bigtriangledown c(\overline{x})^Td=0$$
Il passo produce un miglioramento nel valore di $f(x)$ SE e SOLO se 
$$\bigtriangledown f(\overline{x})^Td<0$$
Quindi un passo migliorante da $\overline{x}$ NON è possibile SE e SOLO SE
$$\exists \overline{\lambda} \neq 0: \bigtriangledown c(\overline{x}) = \overline{\lambda}\bigtriangledown f(\overline{x})$$
es
Abbiamo $\bigtriangledown f$ che punta sempre in alto mentre il vincolo di uguaglianza è la circonferenza
In $x^*$ si ha una direzione opposta a quella di $\bigtriangledown f$, quindi i due vettori sono allineati
![[Pasted image 20240403085614.png|300]]

Un modo alternativo di formulare la stessa condizione di ottimalità in un punto $\overline{x}$, consiste nell'introdurre la funzione Lagrangiana (in cui combiniamo la funzione obiettivo con la quantita di quanto viola il vincolo $c(x)$). Derivando tutto ottengo la derivata della funzione obiettivo meno la derivata di $c(x)$
$$L(x, \lambda) = f(x)-\lambda c(x)$$
$$\bigtriangledown_xL(x, \lambda) = \bigtriangledown f(x) - \lambda\bigtriangledown c(x)$$
Quindi la condizione di ottimalità di $\overline{x}$ equivale alla condizione
$$\exists \overline{\lambda} \neq 0: \bigtriangledown_xL(\overline{x}, \overline{\lambda}) = 0$$

Si tratta di una condizione necessaria del primo ordine MA non sufficiente (come nel caso non vincolato QUINDI è un modo per ricondursi da vincolato a non vincolato)