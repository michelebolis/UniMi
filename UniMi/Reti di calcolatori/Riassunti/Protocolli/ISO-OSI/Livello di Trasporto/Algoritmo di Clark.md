Situazione: `produttore veloce e consumatore lento`

`Silly Window Syndrome`: in alcune AP si potrebbe richiedere di leggere o inviare un basso numero di byte, intasando la rete con moltissimi segmenti

Lato ricevente, ipotizziamo che l'applicazione legga un byte alla volta.
MA ogni volta che si libera la finestra, dovrei inviare un ACK solo per notificare una finestra di 1 byte e la sorgente invierebbe un segmento solo per un byte (con un header da ... byte)

Soluzione: algoritmo di Clark
Si evita di annunciare la nuova disponibilita di window aspettando o di raggiungere il MSS o se ho almeno meta buffer vuoto

1. $X = min(W_R, buffer/2)$
2. $TempoNoWinUpdate = X*TempoConsumo$