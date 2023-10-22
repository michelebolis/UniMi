Consideriamo A e B collegati da un solo cavo
- Tempo di trasmissione $T_x = {datiDaTrasmettere \over capacitaCanale}$  
	- dipende dalla capacita del canale e dalla velocità di immissione del mittente.
- Tempo di propagazione $T_p = {distanza \over velocita}$ 
	- è il tempo che un pacchetto impiega da A a B
	- dipende unicamente dalle caratteristiche fisiche del canale su cui viaggiano i dati (lunghezza e materiale fisico)
- $T_p+T_x$ tempo che intercorre da quando il primo bit esce a quando l ultimo bit arriva
	- $T_p$ aumenta molto fino a superare Tx quando le distanze aumentano (comunicazioni satellitari, continentali)

Anche l'ACK è un pacchetto, che viaggia nella direzione opposta quindi dobbiamo considerare anche $T_xACK$ e il $T_pACK$.
OSS $T_p$ e $T_pACK$ sono uguali, perche è lo stesso canale e la stessa distanza 
$T_xACK$ vogliamo che si minimizzi: per far ciò minimizziamo il peso dell'ACK, tanto da risultare spesso irrilevante nella stima del tempo.

Per riconoscere che non sia arrivato un ACK, faccio trascorrere un tempo minimo calcolato come: $T_x + 2*T_p$

In $T_p$ consideriamo il tempo del singolo bit perche la capienza del messaggio totale è utilizzata nel calcolo di $T_xP_1$

[[Jitter]]