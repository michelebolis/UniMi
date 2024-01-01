Consideriamo due nodi A e B collegati da un solo cavo
- Tempo di trasmissione $T_x = {datiDaTrasmettere \over capacitaCanale}$  
	- dipende dalla capacita del canale e dalla velocità di immissione del mittente.
	- per tutto il tempo $T_x$ il driver sicuramente è occupato
- Tempo di propagazione $T_p = {distanza \over velocita}$ 
	- è il tempo che un pacchetto impiega ad arrivare da A a B
	- dipende unicamente dalle caratteristiche fisiche del canale su cui viaggiano i dati (lunghezza e materiale fisico)
	- In $T_p$ consideriamo il tempo del singolo bit perche la capienza del messaggio totale è utilizzata nel calcolo di $T_xP_1$
- $T_p+T_x$ tempo che intercorre da quando il primo bit esce a quando l'ultimo bit arriva
	- $T_p$ aumenta molto fino a superare $T_x$ quando le distanze aumentano (comunicazioni satellitari, continentali)
- RTT Round Trip Time: tempo dall'invio del primo frame all'arrivo dell'ultimo ACK

Dati questi tempi ricaviamo l'[[Efficienza della rete]]
[[Dimensionamento clock]]
[[Jitter]]