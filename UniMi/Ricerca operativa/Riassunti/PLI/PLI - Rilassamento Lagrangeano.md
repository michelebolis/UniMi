Il rilassamento Lagrangeano $LR$ di un problema di ottimizzazione lineare discreto $P$ si ottiene `rimuovendo alcuni vincoli e aggiungendo all'obiettivo termini di penalità per la loro violazione`
$$P: min\{z(x): Ax \leq b, x \in X \subseteq Z^n_+\}$$
$$LR: min\{z_{LR}(x, \lambda) = z(x) + \lambda (Ax-b) : x \in X \subseteq Z^n_+ \}$$
con $\lambda \geq 0$ moltiplicatori lagrangiani

Esso soddisfa le condizioni per essere un rilassamento
- Vincoli: $\{x: Ax \leq b, x \in X\} \subseteq \{x:x \in X\}$
- Obiettivo
	- $Ax -b \leq 0$ per tutte le soluzioni ammissibili per $P$
	- $\lambda (Ax-b) \leq 0$ per tutte le soluzioni ammissibili per $P$
	- $z_{LR}(x, \lambda) = z(x) + \lambda (Ax-b) \leq 0$ per tutte le soluzioni ammissibili per $P$