La scelta del dimensionamento dell RTO è un fattore critico delle performance
La scelta dell RTO deve essere dinamica
Quando si apre una connessione, non abbiamo informazioni sulla rete, quindi ci si basa sullo standard RFC 2988
Come outliner consideriamo il caso in cui l'ACK si perda

Utilizziamo una distribuzione normale con media e deviazione standard
Considerando l RTO come un outliner: $\mu + k*\sigma$

Fasi:

---
- $T_0$ Momento in cui la connessione viene aperta: 

Non ho informazioni sul RTT (Round Trip Time: da quando mando il segmento a quando ricevo l ACK). 
Imposto RTO a 3 secondi. 
Mantengo due variabili: 
- SRTT = NULL (Smoothing RTT stima $\mu$) 
- RTTVAR = NULL (RTT Variance stima $\sigma$) e poi G <= 100ms (G è la granularita del clock)

SE al $T_0$ scade l'RTO, raddoppio l'RTO (fino a un massimo di 2 minuti) in quanto non ho informazioni

---
- $T_1$ Momento in cui ricevo un segmento di ACK con un RTT = R

Imposto SRTT = R e RTTVAR = R/2. $$RTO = R + max(G, k*RTTVAR)$$con $k = 4$ (suggerito)
es 
$R = 10 ms$, 
$RTO = 10ms + 4*5ms = 30ms$, quindi da 3 secondi siamo passati a 30ms

---
- $T_k$, con $k>2$, quando arriva un RTT = R, 

Con $0<\beta<1$, imposto $$RTTVAR = (1-\beta)*RTTVAR + \beta*|SRTT-R|,$$
OSS piu $\beta$ è vicino a 0, piu tenderò ad aggiornare meno il mio valore
- Piu $\beta$ è alto, piu sono sensibile agli sbalzi di R MA se è solo un rumore temporaneo rischio di cambiare troppo
- Piu $\beta$ è basso, piu RTTVAR è smussato MA non cattura una variazione

Con $0<\alpha<1$, imposto $$SRTT = (1-\alpha)*SRTT + \alpha*R$$Standard $\alpha=1/8$ e $\beta=1/4$)
Di conseguenza aggiornero l'RTO come 
$$RTO = SRTT + max(G, k*RTTVAR)$$con $k = 4$
SE a $T_k$ RTO scade, raddoppio e poi quando riceverò R faro di nuovo la stima

---
Problemi:
Quando l RTO scade, viene raddoppiato E viene ritrasmesso il segmento. MA se l'ACK del segmento precedente arriva molto dopo, ho un ambiguità perche non si capisce a quale trasmissione del segmento appartiene. 

L'algoritmo di Karn dice che ogni volta che raddoppio RTO non considero RTT di nessuno dei due segmenti, non aggiornando quindi ne la media ne la varianza.