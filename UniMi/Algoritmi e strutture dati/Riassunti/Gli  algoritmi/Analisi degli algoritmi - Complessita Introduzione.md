Complessità di algoritmi, tempo: $tempo(I)$ = tempo impiegato da $A$ su input/istanza $I$
La complessità in tempo viene definita come funzione $T: N -> N$ della lunghezza dell'input
- Caso peggiore
$T_{worst}: N -> N$, tempo massimo utilizzato su input di lunghezza $n$
$T_{worst}(n) = max\{tempo(I) | |I|=n\}$

- Caso migliore
$T_{best}: N -> N$, tempo minimo utilizzato su input di lunghezza $n$
$T_{best}(n) = min\{tempo(I) | |I|=n\}$

- Caso medio
$T_{avg}: N -> N$, media dei tempi utilizzati su input di lunghezza $n$ pesata con le probabilità
$T_{avg}(n)= \sum _{|I|=n} Prob(I)*tempo(I)$

Limitazione per la complessità del problema
$A$ algoritmo
$R$ risorsa (tempo)
$F: N -> N$ funzione
$P$ problema

- Superiore, upper bound

$A$ ha costo di esecuzione $O(f(n))$ rispetto a $R$ SE la quantità di $R$, sufficiente per eseguire $A$ istanze di lunghezza $n$, è O$(f(n))$

$P$ ha complessità $O(f(n))$ rispetto a $R$ quando esiste un algoritmo che risolve $P$ il cui costo di esecuzione è O(f(n)) rispetto a $R$

- Inferiore, lower bound

$A$ ha costo di esecuzione $\Omega(f(n))$ rispetto a $R$ se la quantità di $R$, necessaria per eseguire $A$ su istanze di lunghezza $n$, è $\Omega(f(n))$

$P$ ha complessità $\Omega(f(n))$ rispetto a $R$ quando ogni algoritmo che risolve $P$ ha costo di esecuzione è $\Omega(f(n))$ rispetto a $R$

Misure di lunghezza dell'input: $|I|$
- Sequenza di $n $elementi: lunghezza dell'input sarà $n$ ma sarebbe $n*bit$ di lunghezza ($n*costante$)

Funzione polinomiale $n^2$
Funzione esponenziale $2^n$

Gli algoritmi il cui tempo di lavoro è limitato da un polinomio sono considerati ragionevoli/praticabili mentre quelli con tempo esponenziali sono considerati impraticabili

Gli algoritmi esponenziali non traggono beneficio significativo da un HW più veloce

![[Pasted image 20240329095854.png|300]]
![[Pasted image 20240329095905.png|300]]