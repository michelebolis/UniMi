Il mittente quando invia il primo segmento con SEQ, setta anche un `RTO Rentrasmission Time Out`. 
Al suo scadere, viene inviato nuovamente il segmento MA con un altra X

SE però il primo segmento in realta era arrivato al ricevente e riesce ad arrivare al mittente, quest'ultimo lo interpreta come errato e quindi abortisce la connessione al ricevente con un $RST=1$.