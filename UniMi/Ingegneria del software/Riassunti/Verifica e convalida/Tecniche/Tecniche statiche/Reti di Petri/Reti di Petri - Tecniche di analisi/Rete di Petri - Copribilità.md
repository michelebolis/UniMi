Una marcatura $M$ `copre` una marcatura $M'$ SE e SOLO SE $\forall p \in P, M(p) \geq M'(p)$
I posti per cui $M(p) > M'(p)$ si dice che sono `coperti in maniera propria`
Una marcatura M è `copribile` a partire da una marcatura M' SE esiste una marcatura $M'' \in R(P/T, M')$ che copre M

SE $M$ è la copertura minima per abilitare $t$, allora la transizione $t$ è morta SE e SOLO SE $M$ non è copribile a partire dalla marcatura corrente
$$\forall p \in pre(t), M(p) = W(<p,t>)$$$$\forall p \in P \text{ } \backslash \text{ } pre(t), M(p) = 0$$
Si conclude quindi che se una marcatura ne copre un’altra, tutte le azioni possibili nella prima **sono possibili** anche nella seconda
È importante notare come le transizioni che erano **abilitate** in una certa marcatura $M'$ lo saranno anche in una marcatura diversa che copre $M'$, a meno che non ci siano **archi inibitori**.