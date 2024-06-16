Regole di branching n-ario

- Branching su una `variabile intera`

Viene selezionata una variabile intera $x \in [1, ..., n]$
Vengono generati $n$ sotto problemi fissando $x=1$, $...$, $x=n$

- Branching su $n$ `variabili binarie`

Viene scelto un vettore di $n$ variabili binarie ($x_1$, ..., $x_n$)
Vengono generati $n+1$ sotto problemi fissando alcune variabili (una riga per ogni problema)
Potrebbe sembrare che si generi un albero sbilanciato se una parte scelgo un numero piu alto/basso di variabili rispetto ad un altra zona. Di solito gli alberi di branch si cerca di tenerli bilanciati MA in realta `ciò che conta non sono il numero di variabili`, ma l'`effetto vincolante delle variabili fissate` (es x=0 non conta niente, x=1 ha un effetto forte)
![[Pasted image 20240327140356.png|300]]

