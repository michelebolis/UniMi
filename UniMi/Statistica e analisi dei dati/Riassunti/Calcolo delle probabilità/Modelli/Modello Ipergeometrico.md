Il modello Ipergeometrico descrive estrazione senza remissione di $n$ oggetti sapendo che sono presenti $N$ oggetti accettabili e $M$ non accettabili
Parametri
- N = |Categoria1|
- M = |Categoria2|
- n = NumeroEstrazioni

$$X \sim H(n,N,M)$$
$f_X(x) = P(X = x) =$ (modi in cui posso estrarre $x$ da $N$ * modi in cui posso estrarre $x$ da $M$) / (combinazioni di $n$ cose da un insieme che ne contiene $N+M$)
//ragiono sull'insieme di $n$ estrazioni
$$f_X(x) = P(X = x) = \frac{\binom{N}{x}*\binom{M}{n-x}}{\binom{N+M}{n}}*I_{\{0,...,n\}}$$
Approccio composizionale

$i = 1, …, n$ le singole estrazioni, $X_i =\begin{cases} 1 \text{ SE i-esimo oggetto è della categoria1} \\ 0 \text{ ALTRIMENTI} \end{cases}$

$X_i\sim B(p)$, con $p = P$(i-esimo oggetto categoria1) ATT senza conoscere quello che è successo prima
$$p=\frac{N}{N+M}$$

$$E(X) = n*\frac{N}{N+M}$$
DIM
$E(X) = E(\sum_{i=1}^n X_i) = \sum_{i=1}^n E(X_i) = np = n*\frac{N}{N+M}$

OSS $np$ ci ricorda il binomiale, l unica differenza è la reimmisione

$$Var(X)=np*(1-p)*(1-\frac{n-1}{N+M-1})$$
DIM
$Var(X_i)=p*(1-p) = \frac{N}{N+M}*\frac{M}{N+M}$
$Var(X) = Var(\sum_{i=1}^n X_i)$ MA le $X_i$ devono essere indipendenti

Prendendo un $X_i$ $X_j$, il segno della covarianza mi aspetto sia negativo
$Cov(X_i,X_j) = E(X_i*X_j)-E(X_i)*E(X_j)$
$X_i*X_j= \begin{cases} 1 \text{ SE } X_i=X_j=1\\ 0 \text{ ALTRIMENTI } \end{cases}$ 
$= P(X_i=1,X_j=1)-(\frac{N}{N+M})^2$
$=P(X_i=1|X_j=1)*P(X_j=1)-(\frac{N}{N+M})^2$ // Usando la regola di fattorizzazione
$P(X_j=1)=\frac{n*N}{N+M}$
$P(X_i=1|X_j=1)=\frac{N-1}{N+M-1}$
$=\frac{N-1}{N+M-1}*\frac{n*N}{N+M}-(\frac{N}{N+M})^2$
$=\frac{N}{N+M}*(n*\frac{N-1}{N+M-1}-\frac{N}{N+M})$
$\frac{N}{N+M}*(\frac{(N+M)*(N-1)-N*(N+M-1)}{(N+M-1)*(N+M)})$
$-\frac{MN}{(N+M)^2*(N+M-1)}$
È negativa come ci aspettavamo

$Var(X) = Var(\sum_{i=1}^n X_i)=\sum_{i=1}^n Var(X_i) + \sum_{i\neq j}Cov(X_i,X_j)$
$=n*\frac{N}{N+M}*\frac{M}{N+M}-n*(n-1)*\frac{MN}{(N+M)^2*(N+M-1)}$
$= \frac{nNM}{(N+M)^2}*(1-\frac{n-1}{N+M-1})$
$=np*(1-p)*(1-\frac{n-1}{N+M-1})$

SE numero di palline aumenta, $N+M$ tende a infinito, 1-0 --> Varianza tende a quella binomiale