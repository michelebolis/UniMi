Una rete di Petri con marcatura $M_0$ si dice conservativa rispetto alla funzione $H: P -> N^+$ SE e SOLO SE
$$\forall M \in R(P/T, M_0), \sum_{p \in P}H(p)M(p) = \sum_{p\in P} H(p)M_0(p)$$
Una rete di Petri è conservativa in una marcatura M SE esiste almeno una funzione H per cui è conservativa

Una rete di Petri con marcatura M conservativa rispetto a una funzione che assegna tutti pesi uguali, si dice strettamente conservativa
1. Il numero di gettoni è conservato e resta uguale in tutte le marcature
$$\forall M \in R(P/T, M_0), \sum_{p \in P}M(p) = \sum_{p\in P} M_0(p)$$

2. Il numero di gettoni distrutti dallo scatto di una transizione è uguale al numero di gettoni che crea
$$\forall t \in T, \sum_{p\in pre(t)} W(<p, t>) = \sum_{p \in post(t)}W(<t,p>)$$

