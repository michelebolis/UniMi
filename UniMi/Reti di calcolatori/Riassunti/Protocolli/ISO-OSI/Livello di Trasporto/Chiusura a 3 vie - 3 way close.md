Situazione: il client chiede la chiusura della connessione nonostante non abbia ricevuto tutti gli ACK
Il server ha ancora dei segmenti di cui deve mandare l'ACK

1. L'applicazione del server, ricevendo EOF, fa la close()
2. MA dato che deve mandare al client un ACK, manda insieme flag FIN, ACK, ACK=X+N (con N ACK mancanti)
3. Client infine manderà ACK, ACK = Y+1