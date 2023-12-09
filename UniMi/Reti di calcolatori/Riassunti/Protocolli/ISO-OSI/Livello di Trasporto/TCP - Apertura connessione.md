Sia la sorgente che la destinazione scelgono un SEQ SequenceNumber 
Oggi non viene piu usato un approccio incrementale ma viene usata una funzione crittografica

SEQ non parte sempre da 0, per evitare che segmenti di una vecchia connessione ancora nella rete causino sovrapposizione

Fasi
1. La sorgente invia una richiesta di connessione, un segmento in cui flag SYN=1 comunicando la propria SEQ(X) (ACK non verra guardato perche il flag è a 0). Il sorgente è in stato di SYN SEN (Sent)
2. Il ricevitore controlla il checksum e, se corretto, risponde con un segmento in cui SYN=1 e ACK=1 comunicando il proprio SEQ(Y) e ACK che sarà X+1. Il ricevente entra in stato di SYN RECV (Received). (ACK = Ciò che mi aspetto ora -> ho ricevuto X, ora mi aspetto X+1)
3. La sorgente è ora in stato di connessione established il ricevente non sa se la sorgente ha ricevuto il segmento precedente, quindi viene inviato un segmento al ricevente con ACK=1 e ACK=Y+1
4. Ora entrambi hanno una connessione bidirezionale indipendente (indipendente perche ci sono due SEQ indipendenti)

Problemi possibili:
- Non c è una porta in ascolto nella socket ricevente. Viene mandato (al punto 2) un segmento con RST=1
- ACK da ricevente a mittente non arriva in tempo. -> [[RTO]]