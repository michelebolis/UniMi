Dato un problema $P = min\{z_P(x) : x \in X(P)\}$
un problema $R = min\{z_R(x) : x \in X(R)\}$
è un rilassamento di P SE valgono
- $X(P) \subseteq X(R)$ //sulle regioni ammissibili
- $z_R(x) \leq z_P(x), \forall x \in X(P)$ //sugli obiettivi
OSS in caso di massimizzazione le disequazioni sono invertite

Corollario: $z^*_R \leq z^*_P$
Ci sono molti tipi di versi di rilassamento
Un rilassamento è tanto migliore quando piu il suo valore ottimo è vicino a $z^*_P$

- Rilassamento lineare continuo
Quando P è un problema di ottimizzazione discreta, il suo rilassamento continuo C è ottenuto da P trascurando le condizioni di integralità
$$P: min\{z(x) \in X, x \in Z^n_+\}$$
$$C: min\{z(x) \in X, x \in R^n_+\}$$
Quando P è un problema di ottimizzazione lineare discreta, il suo rilassamento continuo LP è un problema di programmazione lineare
$$P: min\{cx:Ax \leq b, x \in Z^n_+ \}$$
$$LP: min\{cx:Ax \leq b, x \in R^n_+ \}$$
SE $x^*_{LP} \in Z^n_+$ ALLORA $x^*_P=x^*_{LP}$

- Rilassamenti combinatori
Il rilassamento combinatorio C di un problema di ottimizzazione combinatoria P è ancora un problema di ottimizzazione combinatoria ma tipicamente molto piu facile da risolvere

- Rilassamento Lagrangeano
Il rilassamento Lagrangeano LR di un problema di ottimizzazione lineare discreto P si ottiene rimuovendo alcuni vincoli e aggiungendo all'obiettivo termini di penalità per la loro violazione
$$P: min\{z(x): Ax \leq b, x \in X \subseteq Z^n_+\}$$
$$LR: min\{z_{LR}(x, \lambda) = z(x) + \lambda (Ax-b) : x \in X \subseteq Z^n_+ \}$$
con $\lambda \geq 0$ moltiplicatori lagrangiani

Esso soddisfa le condizioni per essere un rilassamento
- Vincoli: $\{x: Ax \leq b, x \in X\} \subseteq \{x:x \in X\}$
- Obiettivo
	- $Ax -b \leq 0$ per tutte le soluzioni ammissibili per P
	- $\lambda (Ax-b) \leq 0$ per tutte le soluzioni ammissibili per P
	- $z_{LR}(x, \lambda) = z(x) + \lambda (Ax-b) \leq 0$ per tutte le soluzioni ammissibili per P

- Rilassamento surrogato
Il rilassamento surrogato S di un problema di ottimizzazione lineare discreto P si ottiene sostituendo un insieme di vincoli con un loro combinazione convessa
$$P: min\{z(x): Ax \leq b, x \in X \subseteq Z^n_+\}$$
$$LR: min\{z(x) : \lambda ^TAx \leq \lambda^T b, x \in X \subseteq Z^n_+\}$$
con $\lambda \geq 0$

Esso soddisfa le condizioni per essere un rilassamento
- Vincoli: $Ax \leq b$ implica $\lambda ^TAx \leq \lambda^T b$ MA non viceversa
- Obiettivo: non cambia


Si puo dimostrare che, scegliendo i migliori moltiplicatori $\lambda$, in caso di minimizzazione
$$z^*_{LP} \leq z^*_{LR} \leq  z^*_S \leq z^*$$
