Il termine processo viene utilizzato per indicare qualcosa che ha uno svolgimento nel tempo
Processi stocastici: c è un indice temporale continuo/discreto in cui a instanti casuali succedono qualcosa
La casualità è legata all attimo di tempo in cui succedono

Normalmente sono interessato al conteggio in un certo tempo
$t$ tempo con $t = 0$ l'istante iniziale
$N(t) =$ numero di eventi che accadono in $(0, t]$
$N$ sarà una variabile aleatoria perché il valore non è noto a priori, dipende dalla casualità degli eventi $E$ perché $N$ sarà un numero

Variabile aleatoria che dipende da un parametro fissato
Senza fissare $t$, $N$ diventa una famiglia di variabili aleatorie e si chiama processo stocastico
Una famiglia di processi stocastici è quella del processo di Poisson

Processo di Poisson SE:
1. $N(0) = 0$
2. Considerando due intervalli di tempi disgiunti, ho quindi due variabili aleatorie, ALLORA le due variabili aleatorie sono indipendenti. Intervalli disgiunti --> indipendenza
3. La distribuzione dei conteggi dipende dalla lunghezza dell'intervallo e NON dai suoi estremi
4. $$\lim_{h->0}\frac{P(N(h)=1)}{h}=\lambda$$
	SE $h$ è piccolo, la probabilità che ci sia un solo conteggio è proporzionale alla lunghezza dell'intervallo
5. $$\lim_{h->0}\frac{P(N(h)\geq 2)}{h}=0$$
	$P(N(h) \geq 2) \approx 0$
	SE h è piccolo, non ha senso considerare piu di due avvenimenti

$N(t)\sim P(\lambda t)$
DIM
Fissato $t$, intervallo 0 ------ t->
Fissato $n$, divido l'intervallo in n segmenti uguali, intervallo $0 - \frac{t}{n} - \frac{2t}{n} - … - t$ ->
Immaginando $n\geq k$, $P(N(t) = k)$ una volta fissato $k$ ho infinite scelte per $n$
I modi in cui posso avere gli avvenimenti possono essere in sotto intervalli diversi perché ho $n$ sotto intervalli $\geq k$
Considerando
- A = ogni avvenimento accade in un diverso intervallo
- B = tutte le altre possibilità

$P(N(t)=k)=P(A\cup B)=P(A)+P(B)$
MA per 5) la $P$ che ci siano due accadimenti nello stesso intervallo è trascurabile, QUINDI quando per $n->\infty$, $P(B) = 0$
Per 4) la probabilità che un accadimento sia in un intervallo è $\lambda*$l'ampiezza dell'intervallo

$= P(A)=\binom{n}{k}*(\lambda*\frac{t}{n})^k*(1-\lambda\frac{t}{n})^{n-k}$
MA $\sim B(n, \lambda\frac{t}{n})$

MA ciò è vero se fisso $n$, MA non fissando n e considerando $n->\infty$
$n*\lambda*\frac{t}{n}=\lambda t$
Ottengo una Poisson $P(\lambda t)$ DIMOSTRATO

Avrei trovato la stessa distribuzione SE avessi considerato un altro intervallo che non iniziasse da 0 ma da $s$ arrivando a $s + t$

Risultato:
Indichiamo $x_1$ l'intertempo da $t = 0$ a $t_1$, $x_2$ da $t_1$ a $t_2$, …
$P(X_1>t) = P(N(t)=0)=e^{-\lambda t}*\frac{(\lambda t)^0}{0!}=e^{-\lambda t}$
$F_{X_1}(t)=P(X_1\leq t)=1-P(X_1>t)=1-e^{-\lambda t}$
QUINDI $X_1 \sim E(\lambda)$

$P(X_2 > t | X_1 = s) = P$(nessun accadimento tra $s$ e $s + t | X_1 = s$)
//in $s$ ho avuto il primo accadimento e dopo $t$ ho avuto un altro accadimento
// $X_1 = s$ e nessun accadimento tra $s$ e $s + t$ sono intervalli disgiunti --> indipendenti
$= P$(nessun accadimento tra s e $s + t) = P(N(t)=0) = e^{-\lambda t}$
QUINDI $X_2 \sim E(\lambda)$

QUINDI $X_1$ e $X_2$ sono indipendenti perché non dipendono da $s$
Ho quindi relazione tra l'esponenziale e il Poisson, SE guardo gli intertempi legati alla distribuzione di Poisson sono esponenziali
MA QUINDI $\forall X_i \sim E(\lambda)$
