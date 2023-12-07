Quanti segmenti possiamo mandare alla destinazione e la velocita di processamento alla destinazione
Lavoriamo a livello dei buffer delle socket (ricordiamo a livello kernel)

Introduciamo 2 variabili: W_S (Finestra di invio) e W_R (Finestra di ricezione) che utilizzeremo nell header del TCP in window size
Lato ricezione, notifica che la W_R = 2000, cioe ho un buffer di 2000byte (Window adv...) con un segmento con window size = 2000
Essendo a livello di trasporto, non sapro quando l applicazione leggera dal buffer (in generale utilizzera le primitive)
Quando la destinazione invia il secondo messaggio nello start della connessione, viene inclusa anche la window size, cioe la $W_R$

Ipotizziamo di avere nella sorgente un W_S= 2000
Dopo l invio di un messaggio da 500, diminuisco W_S di 500 a 1500
Invio un secondo messaggio quindi W_S=1000, e un terzo messaggio W_S=500 e un quarto arrivando con un W_S = 0.
La sorgente blocca l invio dei segmenti che avrebbe ancora da spedire aspettando che il buffer lato ricezione si svuoti

Lato destinazione, i segmenti vengono conservati nei buffer di TCP (e poi inviati al buffer dell applicazione) e l ACK (ipotizzando sia cumulativo) viene mandato alla ricezione dell ultimo segmento CON window size a 0 perche il buffer dell applicazione è pieno 

Dopo del tempo, l applicazione legge 1000 byte, quindi nel buffer dell applicazione vengono tolti 2 segmenti. Il ricevente manda quindi un segmento di ACK (con l ACK dell ultimo segmento) e con WIN=1000

Problema: l unico modo in cui riavvio l invio di segmenti è con l ACK con WIN = ...
SE tale segmento viene perso, e non c è una soluzione, si va in deadlock

La soluzione è utilizzare un Persist Timer al cui scadere il mittente mando un segmento con 1 byte di data. SE perdo tale segmento, potro inviarlo nuovamente allo scadere del Timer.
Alla ricezione, viene riconosciuto come messaggio Window Probe e viene inviato nuovamente l ACK con WIN = ... e ACK = X + 2001 


Silly Window Syndrome
Lato ricevente, ipotizziamo che l applicazione legga un byte alla volta.
MA ogni volta che si libera la finestra dovrei inviare un ACK solo per notificare una finestra di 1 byte e la sorgente invierebbe un segmento solo per un byte (con un header da ... byte)

Soluzione: algoritmo di Clark
Evitare di annunciare la nuova disponibilita di window aspettando o di raggiungere il MSS o se ho almeno meta buffer vuoto