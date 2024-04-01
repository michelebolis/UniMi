Classe $P$: classe dei problemi che possono essere risolti in tempo polinomiale rispetto alla lunghezza dell'input:
- Ordinamento
- Prodotto di matrici
- Ricerca in un array
- …

$n$: lunghezza dell'input
$s, t: N --> N$ funzioni
$TIME(t(n))=$ classe dei problemi di decisione risolubili da algoritmi in tempo $O(t(n))$
$SPACE(s(n))=$ classe dei problemi di decisione risolubili da algoritmi in spazio $O(s(n))$

Es 𝜋 = stabilire SE un array ordinato contiene una chiave $\exists x \in TIME(\log n)$

Classe $P = \bigcup _{c=0}^{\infty} TIME(n^c)$ è la classe dei problemi di decisione risolubili in tempo polinomiale rispetto alla lunghezza dell'input
Classe $PSPACE= \bigcup_{c=0}^{\infty} SPACE(n^c)$ spazio polinomiale
Classe $EXPTIME= \bigcup_{c=0}^{\infty} TIME(2^{nc})$

$P \subseteq EXPTIME$

- In tempo $t$ quanto spazio riusciamo a utilizzare?
In ogni istruzione macchina visita al massimo k celle di memoria
Numero celle visitate in tempo $t \leq k*t$
$Spazio \leq k*tempo$
$Spazio= O(tempo)$

$P \subseteq PSPACE$

- In spazio $s$ quanto tempo posso utilizzare?
s celle di memoria con k bit ciascuna
$k*s$ bit in totale
$2^{k*s}$ configurazioni diverse

Programma con $p$ istruzioni
Numero tot $p*2^{ks}$
SE $t> p*2^{ks}$ ho un loop infinito

Un programma che termina $t <= p*2^{ks}$
$Tempo \leq exp(spazio)$

$PSPACE \subseteq EXPTIME$

Conclusioni
$P \subseteq PSPACE \subseteq EXPTIME$
$P\neq ECPTIME$

![[Pasted image 20240401171501.png|300]]

Usiamo algoritmi non deterministici
Un istruzione indovina $b \in \{0, 1\}$
L'algoritmo indovina sempre quella giusta SE c'è
```
ALGORITMO sodd(Formula Φ(x1, x2, …, xn)) -> boolean
FOR i<-1 to n DO
	z <- indovina un valore in {0, 1}
r <- Φ(z1, z2, …, zn) //verifica
RETURN r
```

Classe NP: classe dei problemi di decisione risolubili in tempo polinomiale da algoritmi non deterministici, certificati verificabili in tempo polinomiale
es [[Problema di soddisfacibilità]]

$NTIME(f(n))$: insieme dei problemi di decisione risolti da algoritmi non deterministici in tempo $O(f(n))$
$NP = \bigcup_{c=0}^{\infty} NTIME(n^c)$

Es sia il problema di partizione che quello sulle clique appartengono a NP
Nei problemi NP, l'algoritmo ha
- Fase non deterministica in cui costruisce il certificato
- Fase deterministica che verifica il certificato in tempo polinomiale
$P \subseteq NP$

I problemi NP-completi sono problemi piu difficili in NP
$P \subseteq NP \subseteq NPSPACE$
$PSPACE=NPSPACE$
$P \subseteq NP \subseteq PSPACE=NPSPACE \subseteq EXPTIME$

$P\neq NP?$

[[Complessita computazione - Riducibilita tra problemi]]
[[Complessita computazione - Riducibilità polinomiale]]

$\pi$ è NP-HARD / NP-DIFFICILE SE ogni problema $N' \in NP$ è riducibile polinomialmente a $\pi$
$\forall \pi' \in NP, \pi' \leq_p \pi$
$\pi$ è NP-COMPLETO SE $\pi$ è NP-HARD e $\pi \in NP$ 

Teorema: Sia $\pi$ un problema NP-completo
- SE $\pi \in P$ ALLORA $P=NP$
- SE $\pi \notin P$ ALLORA $P\neq NP$
Teorema di Cook: SODD è NP-COMPLETO

DIM
1. $SODD \in NP$
2. $\forall \pi' \in NP, \forall \pi' \leq_p SODD$

![[Pasted image 20240401172535.png|300]]
SE $\pi$ è NP-COMPLETO e $\pi \leq_p \pi'$ con $\pi' \in NP$, ALLORA $\pi'$ è NP-COMPLETO