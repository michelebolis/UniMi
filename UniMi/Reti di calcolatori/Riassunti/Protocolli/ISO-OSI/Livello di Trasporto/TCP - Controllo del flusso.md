Il campo `Window Size` di ogni segmento indica il numero di byte che il TCP ricevente puo ricevere nel buffer. In questo modo si garantisce che ci sia sempre spazio libero nel buffer del destinatario prima che la sorgente mandi i dati.

Introduciamo 2 variabili: $W_S$ (`Finestra di invio`) e $W_R$ (`Finestra di ricezione`) che utilizzeremo nell'header del TCP in window size

Il flusso si ferma quando $W_S$ = 0 
$W_R$ invece è aumentata quando la destinazione riceve dei dati privi di errore mentre viene diminuita quando AP destinatario legge dei byte dal buffer

[[TCP - Controllo del flusso Esempio]]

- Perdita dell'ACK -> [[Persistent Timer]]
- Silly Window Syndrome -> [[Algoritmo di Clark]]
