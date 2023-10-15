Consideriamo A e B collegati da un solo cavo
- Tempo di trasmissione $T_x = {datiDaTrasmettere \over capacitaCanale}$  
	- dipende dalla capacita del canale e dalla velocità di immissione del mittente.
- Tempo di propagazione $T_p = {distanza \over velocita}$ 
	- è il tempo che un pacchetto impiega da A a B
	- dipende unicamente dalle caratteristiche fisiche del canale su cui viaggiano i dati (lunghezza e materiale fisico)
- $T_p+T_x$ tempo che intercorre da quando il primo bit esce a quando l ultimo bit arriva
	- $T_p$ aumenta molto fino a superare Tx quando le distanze aumentano (comunicazioni satellitari, continentali)

Anche l'ACK è un pacchetto, che viaggia nella direzione opposta quindi dobbiamo considerare anche $T_xACK$ e il $T_pACK$
OSS $T_p$ e $T_pACK$ sono uguali, perche è lo stesso canale e la stessa distanza 
$T_xACK$ vogliamo che si minimizzi: per far ciò minimizziamo il peso dell'ACK, tanto da risultare spesso irrilevante nella stima del tempo.

Per riconoscere che non sia arrivato un ACK, faccio trascorrere un tempo minimo calcolato come: $T_x + 2*T_p$

In $T_p$ consideriamo il tempo del singolo bit perche la capienza del messaggio totale è utilizzata nel calcolo di $T_xP_1$

In un caso piu generale oltre al tempo di propagazione del canale in se abbiamo piu router coinvolti, ognuna con le proprie code che causano un tempo di coda $T_q$.
Il tempo complessivo è piu complicato da stimare

Tempo di invio completo: $T_x+ T_p + T_q + T_xR_1 +$ ...
$T_q$: tempo di coda nel singolo router


I tempi variabili della rete sono i tempi delle code, in quanto non so quanto sono piene e quindi quando l algoritmo decodificherà il pacchetto
In questo caso le code sono di tipo store and forward. 
Il tempo indefinito è quello che intercorre tra forward e store: Jitter.
Quanti piu nodi di reti devo attraversare, tanto piu Jitter aggiungo e quindi tanto piu la media per i pacchetti aumenterà. Sara quindi necessario una stima adattiva 

Il Jitter è definito dalla deviazione standard, importante per alcuni applicativi che necessitano stabilità di comunicazione (es videogiochi)
La media è comunque importante 