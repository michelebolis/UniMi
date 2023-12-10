La ritrasmissione dei frame coinvolti nella collisione avviene quindi dopo un tempo $\tau$ casuale ottenuto con la tecnica BEB Binary Exponenzial Backoff
$$BEB = [0:2^i-1]*UT$$
con $i$ il numero di collisioni ($1<i<16$) della stazione e $UT$ unità di tempo 

Con il BEB i frame potrebbero ancora collidere se viene generato lo stesso numero di UT ma è probabilisticamente improbabile
OSS CSMA/CD NON garantisce che il frame che arriva senza collisioni sia senza errori

Ogni stazione ha un contatore per generare il numero casuale, in particolare per l'indice $i$ nel BEB
Quanto BEB incide sulle prestazioni: l'algoritmo dilata l'accesso NON garantendo la fairness
E' un algoritmo adattivo al traffico percepito, in quanto dipende dal numero di collisioni $i$