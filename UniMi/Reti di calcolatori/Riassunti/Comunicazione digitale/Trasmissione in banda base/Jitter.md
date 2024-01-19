In un caso piu generale oltre al tempo di propagazione del canale in se abbiamo piu router coinvolti, ognuno con le proprie code che causano un tempo di coda $t_q$.
Il tempo complessivo è piu complicato da stimare

Tempo di invio completo: $t_x+ t_p + t_q + t_xR_1 +$ ...
$T_q$: tempo di coda nel singolo router

*I tempi variabili della rete sono i tempi delle code*, in quanto non so quanto sono piene e quindi quando l algoritmo del router decodificherà il pacchetto

Il tempo indefinito è quello che intercorre tra forward e store: `Jitter`.
Quanti piu nodi di reti devo attraversare, tanto piu Jitter aggiungo e quindi tanto piu la media per i pacchetti aumenterà. Sara quindi necessario una stima adattiva 

Il Jitter è definito dalla deviazione standard della somma dei delay degli store and forward
Risulta essere importante per alcuni applicativi che necessitano stabilità di comunicazione (es videogiochi)

Per risolvere il problema del Jitter, si usa la tecnica di buffering che permette di mantenere un certo numero di pacchetti in una memoria bufferizzati alla destinazione 