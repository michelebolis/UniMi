La ritrasmissione dei frame coinvolti nella collisione avviene quindi dopo un tempo $\tau$ casuale ottenuto con la tecnica `BEB Binary Exponenzial Backoff`
$$BEB = [0:2^i-1]*UT$$
con $i$ il numero di collisioni ($1<i<16$) della stazione e $UT$ unità di tempo 

Con il BEB i frame potrebbero ancora collidere se viene generato lo stesso numero di UT ma è probabilisticamente improbabile
OSS CSMA/CD NON garantisce che il frame che arriva senza collisioni sia senza errori

Ogni stazione ha un contatore per generare il numero casuale, in particolare per l'indice $i$ nel BEB
Svantaggi: l'algoritmo dilata l'accesso NON garantendo la fairness
Vantaggi: è un algoritmo adattivo al traffico percepito, in quanto dipende dal numero di collisioni $i$

Osservando $$U = {t_x \over t_x+2t_p * {1 \over A}}$$
Con: 
- $1 \over A$ = Numero medio di stazioni che deve aspettare prima di accedere
- $A= k*p * (1-p)^{kp}$
- $k$ numero di stazioni
- $p$ probabilità che quella stazione possa accedere al canale 