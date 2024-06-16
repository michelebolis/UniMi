Considerando un problema di PLI con insieme ammissibile
$$X = \{x \in Z^n_+ : Ax \leq b\}$$
dove $A$ ha $m$ righe e $n$ colonne
Scegliamo un vettore $u \in R^n_+$
- $\sum_{j=1}^{n}{ua_jx_j} \leq ub$ è valida perche $ax \leq b$ e $u \geq 0$ 
- $\sum_{j=1}^{n}{\lfloor{ua_j}\rfloor x_j} \leq ub$ è valida perché $x \geq 0$
	- arrotondando per difetto vuol dire `mantenere uguale o diminuire il primo membro`
- $\sum_{j=1}^{n}{\lfloor{ua_j}\rfloor x_j} \leq \lfloor ub \rfloor$ è valida perché $x$ è intero
	- arrotondando per difetto anche il secondo termine vuol dire mantenere uguale o anche il secondo 0

Otteniamo quindi una disuguaglianza valida MA la sua efficienza dipenda dalla scelta di $u$
Ogni disuguaglianza valida puo essere generata con questa procedura in un numero finito di passi
