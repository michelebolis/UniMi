Lato ricevente, ipotizziamo che l'applicazione legga un byte alla volta.
MA ogni volta che si libera la finestra dovrei inviare un ACK solo per notificare una finestra di 1 byte e la sorgente invierebbe un segmento solo per un byte (con un header da ... byte)

Soluzione: algoritmo di Clark
Evitare di annunciare la nuova disponibilita di window aspettando o di raggiungere il MSS o se ho almeno meta buffer vuoto