Una rete di Petri con marcatura $M_0$ si dice `conservativa rispetto alla funzione` $H: P -> N^+$ SE e SOLO SE
$$\forall M \in R(P/T, M_0)\text{, } \sum_{p \in P}H(p)M(p) = \sum_{p\in P} H(p)M_0(p)$$
Ovvero, per ogni marcatura $M'$ raggiungibile dalla marcatura iniziale data una certa marcatura e una funzione $H$, si dice che la rete è conservativa se la sommatoria dei gettoni di ogni posto (quest’ultimi pesati attraverso la funzione $H$) è _**costante** per qualunque marcatura raggiungibile_.
Una rete di Petri è `conservativa in una marcatura` M SE esiste almeno una funzione H per cui è conservativa

Una rete di Petri con marcatura M conservativa rispetto a una funzione che assegna tutti pesi uguali, si dice `strettamente conservativa`
1. Il numero di gettoni è conservato e resta uguale in tutte le marcature
$$\forall M \in R(P/T, M_0), \sum_{p \in P}M(p) = \sum_{p\in P} M_0(p)$$

2. Il numero di gettoni distrutti dallo scatto di una transizione (non morta) è uguale al numero di gettoni che crea
$$\forall t \in T, \sum_{p\in pre(t)} W(<p, t>) = \sum_{p \in post(t)}W(<t,p>)$$

`SE una reti di Petri è conservativa, ALLORA è limitata MA NON viceversa`