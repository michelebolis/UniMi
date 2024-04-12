Si associa ad ogni evento $E$ sullo spazio degli esiti $\Omega$, un numero $P(E)$, la probabilita dell'evento $E$
A1) $\forall E \in A, P(E) \geq 0$
A2) $P(\Omega) = 1$
A3) $\forall E, F \in A, (E \cap F) = \emptyset -> P(E \cup F) = P(E) + P(F)$

Interpretazione frequentista degli assiomi:
A1) il numero di occorrenza non è mai negativo, quindi sicuramente la frequenza relativa è positiva
A2) se un evento si verifica $n$ volte, $\frac{n}{n}=1$
A3) in $n$ ripetizioni, conto le ripetizioni di $E$ e $F$, sommando le conseguenti frequenze relative ottengo la frequenza relativa di $E \cup F$

I tre assiomi $\implies P(E) \leq 1$
OSS SE $(E \cap F) = \emptyset$, $E$ e $F$ sono eventi disgiunti
Posso estendere A3 con piu di 2 Eventi richiedendo che siano disgiunti a 2 a 2, quindi posso estendere l'algebra anche con un numero infinito di eventi (sigma algebra degli eventi)

Per ogni successione di eventi mutuamente esclusivi (t.c. $E_i \cap E_j = \emptyset$ con $i\neq j$ ),
$$P(\bigcup_{i=1}^n E_i) = \sum_{i=1}^nP(E_i)$$
Interpretazione di A3: preso un insieme finito o numerabile di eventi mutuamente esclusivi, la probabilità che se ne verifichi almeno uno è uguale alla somma delle loro probabilita