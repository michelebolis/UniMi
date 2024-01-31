Una rete di Petri con con marcatura M si dice limitata SE e SOLO SE
$$\exists k \in N \text{ t.c. } \forall M' \in R(P/T, M), \forall p\in P, M'(p) \leq k $$
Cioè se è possibile fissare un limite al numero di gettoni della rete

![[Pasted image 20240131084616.png|500]]

SE la rete di Petri è limitata, allora l'insieme di raggiungibilità è finito e quindi esiste un automa a stati finiti corrispondente che ne descrive il comportamento.
Nell'automa gli stati sono le possibili marcature dell'insieme di raggiungibilità.