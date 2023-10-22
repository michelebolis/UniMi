MA tutto quello che abbiamo fatto finora è per una rete a 10Mbit, se vado a 1Gbps?
Cambia la dimensione minima del pacchetto perche cambia $T_x$, in particolare a 512 ns MA $T_p$ non è cambiato e quindi il protocollo non rileva le collisioni
Nello standard sarà necessario cambiare la dimensione minima del frame, in particolare sarebbero necessari 50k bit, diminuendo U moltissimo (es segnale di ACK). 

Un altra soluzione è quella di cambiare il mezzo
La soluzione migliore è diminuire L, la lunghezza totale del canale

Diminuendola da 2.5km a 25m (da nodo ad hub), quindi 25 andata all hub, 25 al nodo, 25 di ritorno da nodo destinazione e altri 25 per tornare al nodo destinazione
$$2*T_p = {10^2 \over {2*10^8}} = 0.5 \micro s$$

Usiamo un compromesso
- 200m di L massimo -> 2$t_p$ su 800m -> 2$t_p$ = 4 microsecondi
- taglie minime di frame a 512Byte. Ho un padding duplice: uno che lo fa fino a 64B ma poi il mio livello fisico aggiunge 512-64 Byte 

Inefficienza
