Situazione: il client ha ricevuto tutti gli ACK e il server non ha niente da fare in sospeso

1. L'applicazione chiama la primitiva close(). Viene mandato il segmento al server con flag FIN=1 e SEQ = X. Il client entra in stato di FIN_WAIT1 
2. Il server, quando riceve il segmento (in particolare l'applicazione receive(EOF)), entra in stato CLOSE_WAIT. Il server manda un segmento con ACK, ACK=X+1 (facendo entrare il client in FIN_WAIT2) e dopo un certo tempo l'applicazione del server chiama la close(), mandando un segmento con FIN e SEQ=Y
3. Quando il client riceve il primo segmento entra in TIMEDWAIT in un loop e manda un segmento ACK, ACK = Y
4. Il server ricevendo l'ACK, fa la close  
5. Lato client dopo 2MSL (Max Segment LifeTime) la socket viene chiusa