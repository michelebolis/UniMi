Dato un problema di ottimizzazione discreta P
$$z^* = max{z(x) : x \in X \subseteq Z^n}$$
L'ottimalità si dimostra calcolando un upper bound $\bar{z}$ e un lower bound $\underline{z}$ t.c. $\underline{z} \leq z \leq \bar{z}$
SE P è di minimizzazione, $\bar{z}$ è primale e $\underline{z}$ è duale
SE P è di massimizzazione, $\underline{z}$ è primale e $\bar{z}$ è duale
La differenza $\bar{z}-\underline{z}$ è detto gap di ottimalità
SE $\bar{z}-\underline{z} = 0$, si ha la garanzia di ottimalità

Un bound primale $\bar{z}$ è dato dal valore della funzione obiettivo $z(x)$ in una qualsiasi soluzione ammissibile $\bar{x} \in X$
$$\bar{z} = z(\bar{x}), \bar{x} \in X$$
Il bound primale puo essere calcolato in vari modi
- algoritmi euristici/meta euristici
- algoritmi di approssimazione con garanzia (in tal caso si ha anche un bound duale)
Per alcuni problemi di ottimizzazione discreta è difficile trovare una soluzione ammissibile

Il bound duale è dato dal valore della funzione obiettivo in z(x) in corrispondenza di una soluzione super ottima $\bar{x}$ in generale non ammissibile