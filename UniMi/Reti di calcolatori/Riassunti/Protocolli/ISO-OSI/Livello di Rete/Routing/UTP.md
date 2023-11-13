WFQ Waited Fair Q
SE voglio differenziare le code in base a diversi livelli di sensibilità del delay, associo ad ogni coda un peso, l equivalente della frazione di canale che assegna al traffico
Scheduling con round robin

(wi / somma k wk) \* RateDisponibile
peso della coda / totale pesi * Rate

es 
con i=1 a 4 wi=4, 2, 2, 2 peso della coda
w1 = 4/10 = 2/5 R
w2,3,4 = 2/10 = 1/5 R

SE canale è da 1Mbps, a w1 assegno 500kb e a ognuno degli altri 125kb
w1 si svuoterà prima delle altre code


Non discrimina secondo il Jitter o il delay richiesto
Tiene conto anche della lunghezza dei pacchetti, restando Fair: ad ogni pacchetti viene dato un timestamp in funzione della categoria e ...
Le code vengono schedulate in base a tale timestamp


SE un router gestisce una coda come WFQ, la slice del canale è determinato dal peso
Alcuni router (solitamente di accesso) fanno shaping, cioè se viene dichiarato all ingresso 1/4 del canale viene verificato se viene prodotto effettivamente 1/4
[[Tecnica Token Bucket]]