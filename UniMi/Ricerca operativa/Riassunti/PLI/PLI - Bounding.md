Il bounding consiste nell'`associare un bound duale ad ogni sotto problema` $F$
Poiché $z^*_R \leq z^*_P$, il valore ottimo $R(F)$ fornisce un bound duale ogni sotto problema $F$
$$z^*_{R(F)} \leq z^*_F$$
Il bound duale è confrontato con un bound primale che corrisponde al valore $z_P(\overline{x})$ di una soluzione ammissibile $\overline{x} \in X(P)$
SE il bound duale di $F$ risulta essere non migliore del bound primale, ALLORA $F$ puo essere scartato
if $z^*_{R(F)} \geq z_P(\overline{x})$ then Fathom $F$

La `correttezza` è data dalla concatenazione di due disuguaglianze
1. Nessuna soluzione puo esistere in $X(F)$ con un valore migliore di $z^*_{R(F)}$ poiché
$$z^*_F \geq z^*_{R(F)}$$
2. $z^*_{R(F)} \geq z_P(\overline{x})$
Concatenando:
$$z_F^* \geq z^*_{R(F)} \geq z_P(\overline{x})$$
Significa che risolvere un problema $F$ all'ottimo è inutile, poiche non fornirà una soluzione migliore di quella gia nota $\overline{x}$

OSS Scartare sotto-problemi è cruciale per risparmiare tempo e memoria

es ho due sottoproblemi divisi da un branching orizzontale. Sapendo che esiste una soluzione ammissibile $\overline{x}$, per il problema rosso la curva di livello che rappresenta la soluzione ottima nel continuo è peggiore della tratteggiata nera, quindi il sotto problema rosso puo essere scartato
![[Pasted image 20240327143303.png]]
