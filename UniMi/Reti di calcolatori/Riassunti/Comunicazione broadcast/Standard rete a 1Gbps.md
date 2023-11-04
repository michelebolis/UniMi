MA tutto quello che abbiamo fatto finora è per una rete a 10Mbit, se vado a 1Gbps?
Cambia la dimensione minima del pacchetto perche cambia $T_x$, in particolare a 512 ns MA $T_p$ non è cambiato e quindi il protocollo non rileva le collisioni
Nello standard sarà necessario cambiare la dimensione minima del frame, in particolare sarebbero necessari 50k bit, diminuendo U moltissimo (es segnale di ACK). 

Inizialmente la lunghezza massima del cavo era stata proposta a 15m ma poi era stata rigettata, optando per 200m.
$$2*T_p = {10^2 \over {2*10^8}} = 0.5 \micro s$$

Standard
- 200m di L massimo -> 2$t_p$ su 800m -> 2$t_p$ = 4 ms
- taglie minime di frame a 512Byte (da 64bytes). Ho un padding duplice: uno che lo fa fino a 64B ma poi 1uando un frame con meno di 512 bytes viene trasmesso, la MAC interface del mittente gli aggiungerà un padding per raggiungere la grandezza minima 