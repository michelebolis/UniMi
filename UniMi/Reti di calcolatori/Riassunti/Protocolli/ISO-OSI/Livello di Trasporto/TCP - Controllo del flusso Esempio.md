Lato ricezione, notifica che la $W_R = 2000$, cioe ho un buffer di 2000byte (Window adv...) con un segmento con window size = 2000
Essendo a livello di trasporto, non saprò quando l'applicazione leggera dal buffer (in generale utilizzerà le primitive)
Quando la destinazione invia il secondo messaggio nello start della connessione, viene inclusa anche la window size, cioe la $W_R$

Ipotizziamo di avere nella sorgente un $W_S$= 2000
Dopo l invio di un messaggio da 500, diminuisco $W_S$ di 500 a 1500
Invio un secondo messaggio quindi $W_S$=1000, e un terzo messaggio $W_S$=500 e un quarto arrivando con un $W_S$ = 0.
La sorgente blocca l invio dei segmenti che avrebbe ancora da spedire aspettando che il buffer lato ricezione si svuoti

Lato destinazione, i segmenti vengono conservati nei buffer di TCP (e poi inviati al buffer dell'applicazione) e l'ACK (ipotizzando sia cumulativo) viene mandato alla ricezione dell ultimo segmento CON window size a 0 perche il buffer dell applicazione è pieno 

Dopo del tempo, l applicazione legge 1000 byte, quindi nel buffer dell applicazione vengono tolti 2 segmenti. Il ricevente manda quindi un segmento di ACK (con l ACK dell ultimo segmento) e con WIN=1000