Un vincolo di disuguaglianza $j \in I$ è attivo in una soluzione $\overline{x}$ SE e SOLO SE $g_j(\overline{x})=0$
L'insieme attivo $A(\overline{x})$ è l'insieme dei vincoli attivi in $\overline{x}$
In ogni punto $\overline{x}$ ammissibile, $A(\overline{x})$ comprende sempre tutti i vincoli di uguaglianza

Considerando un vincolo di disuguaglianza $g(x) \geq 0$ ed un punto $\overline{x}$ su di esso
Il gradiente $\bigtriangledown  g(x)$ è un vettore che punta verso l'interno della regione ammissibile, dato che il vincolo è nella forma $g(x) \geq 0$ ($\leq 0$ nel caso la funzione obiettivo sia massimizzare)

Il punto $\overline{x}$ NON è ottimo SE esiste uno spostamento infinitesimo $d$ tale da migliorare il valore dell'obiettivo e da mantenere l'ammissibilità
$$\bigtriangledown f(\overline{x})d <0$$
$$\bigtriangledown g(\overline{x})d \geq 0$$
Tali condizioni NON possono essere vere entrambe SOLO SE
$$\exists \overline{\lambda} \geq 0: \bigtriangledown f(\overline{x}) =  \overline{\lambda} \bigtriangledown g(\overline{x})$$
(cioè quando puntano nella stessa direzione e stesso verso)

Quando invece il punto $\overline{x}$ NON è sul vincolo, allora si puo avere uno spostamento infinitesimo ammissibile $d$ ammissibile E migliorante quando d è abbastanza piccolo da non superare lo slack del vincolo e 
$$\bigtriangledown f(\overline{x})d <0$$
Quindi la condizione necessaria del primo ordine per l'ottimalità in $\overline{x}$ è la stessa del caso non vincolato
$$\bigtriangledown f(\overline{x}) =0$$
es
![[Pasted image 20240403091749.png|300]]

Un modo alternativo di formulare la stessa condizione di ottimalità in un punto $\overline{x}$ consiste nell'introdurre la funzione Lagrangiana si ha
$$L(x, \lambda) = f(x)-\lambda g(x)$$
$$\bigtriangledown_xL(x, \lambda) = \bigtriangledown f(x) - \lambda\bigtriangledown g(x)$$
Quindi al condizione di ottimalità di $\overline{x}$
$$\begin{cases} \exists \overline{\lambda} \geq 0: \bigtriangledown f(\overline{x}) =  \overline{\lambda} \bigtriangledown g(\overline{x}) \text{ SE }  g(\overline{x})=0
\\ \bigtriangledown f(\overline{x}) = 0 \text{ SE } g(\overline{x})>0 \end{cases}$$
Equivale alle condizioni
$$\exists \overline{\lambda} \geq 0:\bigtriangledown_xL(x, \lambda) = 0$$
$$\overline{\lambda}g(\overline{x})=0$$
