L'`insieme di raggiungibilità` di una rete, a partire da una marcatura $M$, è il piu piccolo insieme di marcature t.c.
- Base: La marcatura $M$ appartenga all'insieme di raggiungibilità con $P/T$ la rete post-transizioni
$$M \in R(P / T, M_0)$$
- Induzione: SE $M'$ appartiene all'insieme di raggiungibilità, ed esiste una transizione per cui è abilitata in $M'$ e porta in $M''$, allora $M''$ è raggiungibile
$$(M' \in R(P/T,\text{ }M) \wedge \exists t \in T,\text{ }M'[t > M'') \implies M'' \in R(P/T,\text{ }M)$$