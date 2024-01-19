Problema: l'unico modo in cui riavvio l'invio di segmenti è con l'ACK da destinazione a sorgente con $WIN = N$
SE tale segmento viene perso si va in deadlock

Per risolvere ciò, quando viene settata la finestra $W_S$, parte un `Persist Timer` che, SE prima del suo scadere, non viene ricevuto un segmento con $WIN = N$, allora TCP manda un `Window Probe`. 
SE perdo tale segmento, potrò inviarlo nuovamente allo scadere del Timer.
Alla ricezione, viene riconosciuto come messaggio Window Probe e viene inviato nuovamente l'ACK con $WIN = N$ e $ACK = X + 2001$