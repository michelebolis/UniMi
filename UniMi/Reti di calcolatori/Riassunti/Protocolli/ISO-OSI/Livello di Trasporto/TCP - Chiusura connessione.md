- Chiusura normale (4 vie/4 way close): client ha ricevuto tutti gli ACK e il sever non ha niente da fare in sospeso
Abbiamo un TCP Client e un TCP Server
Abbiamo inizialmente EST, EST (EST = Established) da entrambi i lati

L'applicazione chiama la primitiva close()
Viene mandato il segmento al server con FIN=1 e SEQ = X
Il client entra in stato di FIN_WAIT1 mentre il server quando riceve il segmento (in particolare l'applicazione receive(EOF)), entra in stato CLOSE_WAIT
Il server manda un segmento con ACK, ACK=X+1 (facendo entrare il client in FIN_WAIT2) e dopo un certo tempo l'applicazione del server chiama la close(), mandando un segmento con FIN e SEQ=Y
Quando lo riceve il client entra in TIMEDWAIT in un loop e manda un segmento ACK, ACK = Y
Il server ricevendo l ACK, fa la close  
Lato client dopo 2MSL (Max Segment Lifetime) la socket viene chiusa

- Chiusura a 3 vie: il client chiede la chiusura nonostante non abbia ricevuto tutti gli ACK
MA nel server ho ancora dei segmenti di cui devo mandare l ACK
L'applicazione del server, ricevendo EOF, fa la close()

MA dato che devo mandare al client un ACK, mando FIN, ACK, ACK=X+N (con N ACK mancanti)
Client mandera ACK, ACK = Y+1

Sia chiusura a 3 che a 4 vie NON ho dati (NON ACK) da inviare

- Chiusura Half-Close: client ha finito di inviare dati MA server deve ancora inviare dati al client
Si usa la primitiva shoutdown() per notificare che si è finito di inviare dati
Anche in questo caso AP del server riceve EOF MA il server non ha finito di inviare, cosi continua con le proprie send(NByte) mandandoli insieme a ACK, ACK = X+1, SEQ = Y, NByte. 
Lato server, avra ora X, EST e lato client avra X, EST
Il canale Server-Client è ancora attivo, riuscendo quindi a mandare l ACK al server per il segmento ricevuto
Si ripete finche l AP del server chiama shoutdown() chiudendo la parte di stream rimanente, mandando un segmento con FIN, SEQ=Y+N
In risposta il client mandera ACK, ACK=Y+N+1


SE il client muore prima di mandare l ACK di chiusura, il server aspetta 2 ore e poi inizia a inviare per 10 volte un KA prob con seq = X-1 ogni 75secondi, SE non risponde, il server chiude la connessione