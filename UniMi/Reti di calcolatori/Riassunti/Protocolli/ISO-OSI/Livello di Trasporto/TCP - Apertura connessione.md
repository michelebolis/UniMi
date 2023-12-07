dobbiamo decidere un sequence number 
Non posso sempre partire da 0 per evitare che pacchetti di una vecchia connessione ancora in giro causino sovrapposizione

Anche nella destinazione ci sara un contatore interno per il SEQ number

1. La sorgente invia una richiesta di connessione, un segmento in cui SYN=1 comunicando la nostra SEQ(X) (ACK non verra guardato perche il flag è a 0). Il sorgente è in stato di SYN SEN (Sent)
2. Il ricevitore controlla il checksum e risponde con un segmento in cui SYN=1 e ACK=1 comunicando il proprio SEQ(Y) e ACK che sara X+1. Il ricevente è in stato di SYN RECV (Received)
3. Il ricevitore è ora in stato di connessione established. MA il ricevente non sa se la sorgente ha ricevuto il segmento precendete, quindi viene inviato un segmento al ricevente con ACK=1 e ACK=Y+1
4. Ora entrambi hanno una connessione bidirezione indipendente (indipendente perche ci sono due SEQ indipendenti)

Oggi non viene piu usato un approccio incrementale ma viene usata una funzione crittografica

Problemi possibili:
- Non c è una porta in ascolto nella socket ricevente. Viene mandato quindi un segmento con RST=1
- ACK da ricevente a mittente non arriva in tempo. Nel mittente qiando viene inviato il suo SEQ, viene settato un RTO Round Time Trip (cioe un timer). MA inviando nuovamente la SEQ con un altra X, la prima in realta era arrivata al ricevente e riesce ad arrivare al mittente che la interpreta come errata e quindi abortisce la connessione al ricevente con un RST=1.