Situazione: il `client ha ricevuto tutti gli ACK e il server non ha niente in sospeso da inviare`

1. L'applicazione sorgente chiama la primitiva `close()`. Viene mandato il segmento al server con flag $FIN=1$ e $SEQ = X$ (con $V(S) = X$). Il client entra in stato di `FIN_WAIT1 `
2. Il server, quando riceve il segmento (in particolare l'applicazione `receive(EOF)`), entra in stato `CLOSE_WAIT` inviando un segmento con $ACK = 1, ACK=X+1$ 
3. Nel frattempo la sorgente, alla ricezione dell'ACK, entra in uno stato di `FIN_WAIT2` attendendo il segmento con FIN dall altro host
4. Dopo un certo tempo, l'applicazione del server chiama la `close()`, mandando un segmento con $FIN = 1$ e $SEQ=Y$ (con $V(R) = Y$), entrando in uno stato di `LAST_ACK`
5. Quando il client riceve il segmento entra in `TIMED_WAIT` in un loop e manda un segmento $ACK = 1$, $ACK = Y$
6. Il server ricevendo l'ACK, chiude la connessione  
7. Lato client dopo $2MSL$ (`Max Segment LifeTime`) la socket viene chiusa