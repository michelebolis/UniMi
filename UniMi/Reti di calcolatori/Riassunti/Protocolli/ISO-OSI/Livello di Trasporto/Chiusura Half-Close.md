Situazione: `il client ha finito di inviare dati MA server deve ancora inviare dati al client`

1. Client usa la primitiva `shoutdown()` per notificare che si è finito di inviare dati. TCP infatti con tale primitiva lascia il path EST in ricezione, mandando il segmento $FIN$ e entrando in `FIN_WAIT1`.
2. Anche in questo caso AP del server riceve EOF MA il server non ha finito di inviare, cosi continua con le proprie `send(NByte)` mandandoli insieme a $ACK = 1$, $ACK = X+1$, $SEQ = Y$, $NByte$. Lato server, avra ora X, EST e lato client avra X, EST. Il canale Server-Client è ancora attivo, riuscendo quindi a mandare l'ACK al server per il segmento ricevuto
3. Quando avra terminato l invio dei dati, l'AP userà a sua volta la primitiva `shutdown()`, e il TCP manderà un segmento di $FIN = 1$, $SEQ =  Y + N$.
4. In risposta, il client manderà $ACK=1$, $ACK=Y+N+1$. Entra cosi in una fase di `TIMED_WAIT` in cui allo scadere del timer di $2MSL$, chiude la connessione
5. Il server, alla ricezione dell'ACK, chiude la connessione