Problema: l'unico modo in cui riavvio l'invio di segmenti è con l'ACK con WIN = ...
SE tale segmento viene perso, e non c è una soluzione, si va in deadlock

La soluzione è utilizzare un Persistent Timer al cui scadere il mittente mando un segmento con 1 byte di data. SE perdo tale segmento, potro inviarlo nuovamente allo scadere del Timer.
Alla ricezione, viene riconosciuto come messaggio Window Probe e viene inviato nuovamente l ACK con WIN = ... e ACK = X + 2001 