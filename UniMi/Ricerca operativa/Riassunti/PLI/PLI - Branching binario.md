Regole di branching comuni
- Branching su una variabile binaria
Viene selezionata una variabile binaria $x$ (solitamente una variabile che ha un valore frazionario, quindi sto impedendo la soluzione del padre)
Due sotto problemi vengono generati fissando $x=0$ e $x=1$ 
- Branching su un vincolo intero
Vengono scelti un vettore di variabili intere ($x_1$, ..., $x_n$), un opportuno vettore di coefficienti interi ($a_1$, ..., $a_n$) e un opportuno termine noto intero $k$
Vengono generati due sotto problemi inserendo i vincoli $ax \leq k$ e $ax \geq k+1$
