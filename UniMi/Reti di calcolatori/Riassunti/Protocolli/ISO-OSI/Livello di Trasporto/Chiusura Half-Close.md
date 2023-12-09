Situazione: il client ha finito di inviare dati MA server deve ancora inviare dati al client

1. Client usa la primitiva shoutdown() per notificare che si è finito di inviare dati
2. Anche in questo caso AP del server riceve EOF MA il server non ha finito di inviare, cosi continua con le proprie send(NByte) mandandoli insieme a ACK, ACK = X+1, SEQ = Y, NByte. 
3. Lato server, avra ora X, EST e lato client avra X, EST. Il canale Server-Client è ancora attivo, riuscendo quindi a mandare l ACK al server per il segmento ricevuto
4. Si ripete finche l AP del server chiama shoutdown() chiudendo la parte di stream rimanente, mandando un segmento con FIN, SEQ=Y+N
5. In risposta il client manderà ACK, ACK=Y+N+1