Come inviare dati da sorgente a destinazione (non è un flusso bidirezionale)
Assumiamo che non ci siano errori nella connessione e che la dimensione dei messaggi al livello applicazione sia maggiore della dimensione del segmento

Sorgente con messaggio da scrivere di 600byte
Sorgente con SEQ = X e destinazione con SEQ = Y
MSS = 500byte

L'applicazione del sorgente scrive il messaggio nel buffer della socket
E' necessario fare due segmenti: uno da 500 e uno da 100

1. Mando il primo segmento con SEQ = X, che conservo nel buffer TCP del mittente con tutti gli altri segmenti
2. Il ricevente controlla che sia il SEQ che si aspettava e lo mette nel buffer ricezione del TCP. Coi suoi tempi i segmenti vengono inviati dal buffer TCP a quello del receiver
3. Il ricevente manda un segmento con ACK=1, ACK = X + 500
4. Il mittente, ricevuto il segmento di ACK, cancello nel buffer TCP il primo segmento e mando il secondo segmento con SEQ=X+500
5. Ricevente ripete passo 2 mandando un ACK=X+600
6. Alla ricezione dell ACK, tutti i segmenti sono stati inviati

Per ottimizzare la trasmissione possono essere inviati piu segmenti e lato ricezione, non viene inviato subito ACK in modo che quando mi arrivi il secondo segmento (quindi in ordine), il ricevente manda un singolo ACK con SEQ dato dalla somma dei due (Cumulative ACK)

NON sempre il cumulative ACK è possibile 


Come mandare dati continuamente (es Secure Shell)
in questi casi hanno nel segmento PSH=1
Lato ricevente, una volta ricevuto il dato, oltre il segmento con ACK, viene mandato un altro segmento al mittente con PSH=1 con lo stesso dato che ha ricevuto

MA è inefficiente

Delay ACK, SE il ricevente ha qualcosa da inviare, mando sia il dato che l ACK del segmento precenìdente.
Quindi il segmento avra PSH=1, ACK=1, Ack=X+1, SEQ=Y, Data='d'

MA viene aggiunto cosi del delay aggiuntivo in cui si aspetta che l applicazione debba inviare qualcosa


Algoritmo di Nagle
Lato sorgente solo quando mi arriva l ACK del primo segmento mando insieme sia il nuovo segmento successivo che l'ACK del segmento precedente

Va bene se l applicazione non debba essere responsive


Manteniamo una variabile sia nel mittente che nel destinatario (Vs/Vr) con la Initial Sequence number 
Assumiamo ACK immediato, che quando arriva alla sorgente questa aggiorna il proprio Vs con X+500
Mandando un secondo messaggio, questo viene perso MA ho trasmesso un terzo messaggio che è arrivato alla destinazione.
Il SEQ è diverso da quello che si aspetta il ricevente, quindi lo conservo nel buffer di TCP SENZA passarlo al buffer dell applicazione
MA non posso rispondere con un ACK X+1000, quindi rispondo con un ACK X+500 perche è quello che mi aspetto
Lato mittente, si aspettava un X+1500, MA non glielo rinvio subito in quanto potrebbe arrivare in ritardo alla destinazione. Nel caso non arrivi pero, viene ignorato il problema e vengono inviati altri segmenti SENZA togliere pero dal buffer il 2o e 3o dal buffer perche non sono arrivati in ordine. Se altri messaggi arrivano al ricevente, verra inviato lo stesso ACK errato precedente, quindi viene ritrasmesso il segmento X+500 (Fast Retrasmitt) che stavolta arriva al ricevente
Il ricevente ha quindi nel buffer i segmenti in "ordine", mandando un ACK cumulativo. La sorgente quando riceve l ACK cumulativo, ripulisce il proprio buffer 

In questo modo lato mittente 3 ACK duplicati triggera il rinvio del primo segmento che stavo aspettando
Questo sistema funziona finche ho qualcosa da trasmettere, difatti non verra mai mandato un ACK al mittente. Per risolvere cio viene introdotto un timer RTO per ogni trasmissione.
Se entro RTO ricevo un altri 3 ACK, allora triggero prima della scadenza del RTO (per questo è un Fast Retrasmission) 

---

TCP è orientato allo stream di byte continuo 


Calibrazione RTO Retrasmission Time Out 
Quando si apre una connessione, non abbiamo informazioni sulla rete, quindi ci si basa sullo standard RFC 2988
Avere una buona stima del tempo medio in cui mi arriva l ACK e come outliner il caso in cui l ACK si perda
Utilizziamo una distribuzione normale con media e deviazione standard
Considero l RTO come un outliner: $\mu + k*\sigma$

- $T_0$ Momento in cui la connessione viene aperta: non ho informazioni sul RTT (Round Trip Time: da quando mando il segmento a quando ricevo l ACK). Imposto RTO a 3 secondi. Mantengono due variabili: SRTT = Null (Smoothing RTT$stima \mu$) e RTTVAR = NULL (RTT Variance stima $\sigma$) e poi G <= 100ms (G è la granularita del clock)
- Momento in cui $T_0$ scade, raddoppio l RTO (Exponential Backoff) in quanto non ho informazioni
- $T_1$ Momento in cui ricevo un segmento di ACK con un round trip time di R, imposto SRTT = R e RTTVAR = R/2. $RTO = R + max(G, k*RTTVAR)$, con k = 4 (suggerito)
es R = 10 ms, $RTO = 10ms + 4*5ms = 30ms$, quindi da 3 secondi siamo passati a 30ms
Non possiamo sempre usare questa formula 
- $T_k, k>2$, quando arriva un round trip time R, imposto $RTTVAR = (1-\beta)*RTTVAR + \beta*|SRTT-R|, con 0<\beta<1$, piu $\beta$ è vicino a 0 piu tenderò ad aggiornare meno il mio valore (Standard $\beta=1/4$)
	- Piu $\beta$ è alto, piu sono sensibile agli sbalzi di R MA se è solo un rumore temporaneo rischio di cambiare troppo
	- Piu \beta è basso, piu RTTVAR è smussato MA non cattura una variazione
  $SRTT = (1-\alpha)*SRTT + \alpha*R, con 0<\alpha<1$, (Standard $\alpha=1/8$)
  Aggiornamento $RTO = SRTT + max(G, k*RTTVAR)$ con k = 4
  SE RTO scade, raddoppio e poi quando ricevero R faro di nuovo la stima

Problemi:
- Quando l RTO scade, viene raddoppiato E viene ritrasmesso il segmento. MA se l ACK del segmento precedente arriva molto dopo, ho un ambiguita perche non si capisce a quale trasmissione del segmento appartiene. L'algoritmo di Karn dice che ogni volta che raddoppio RTO non considero RTT di nessuno dei due segmenti, non aggiornando quindi ne la media ne la varianza.