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