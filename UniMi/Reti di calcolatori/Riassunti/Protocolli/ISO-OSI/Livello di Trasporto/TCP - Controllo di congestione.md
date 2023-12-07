La congestione è un fattore della rete: è determinata dal riempimento delle code nei router e causa la perdita di segmenti
TCP vede la congestione come un errore di trasmissione
thougthput: utilizzamento del canale nel tempo
goodput: thougthput - ritrasmissioni

l obiettivo del TCP quando viene utilizzato per l invio di grandi quantita di dati, è mandare in parallelo piu segmenti possibili

Ipotizziamo di avere la trasmissione di segmenti verso una destinazione in cui in un primo tratto, ho una trasmissione veloce MA poi dal router alla destinazione ho un canale lento (collo di bottiglia). 
SE la rete ce la fa, si nota solo un aumento di RTT
SE i buffer del router si saturano, elimina i segmenti e TCP rileva l errore di trasmissione MA la sorgente come stima quanti segmenti inviare nell unita di tempo?

Finestra di congestione: quanti byte si possono immettere nella rete 
La sorgente sa che se inviato un segmento, ne ricevo l ACK, so che il segmento ha lasciato la rete 
L'unica cosa sicura è l'ACK arrivano con il tempo piu lento della rete, essendo di piccole dimensioni

Variabile $W_C$ (Finestra di congestione) viene aggiunta solo nella sorgente
Caso rete senza congestion
- Ogni volta che ricevo un ACK aumento di uno la $W_C$, risultando in un aumento veloce della finestra (in realta Slow Start con Slow come cauto) fino ad una soglia, slow start threshold
- Ora aumento W_C ogni numero della threshold ACK
- Continuo ad aumentare W_C fino a raggiungere una fase di crociera in cui non lo aumento piu 

$NumeroDiByteChePossoTrasmettere = min(W_C, W_S)$

Problemi:
- RTO scade, NON riceve gli ACK: congestione molto grave in quanto lo scadere del RTO è calcolato come un evento raro
Quando scade l RTO, si riparte con W_C = 1 quindi con uno slow start MA la SlowStartThreshold viene diminuita (in particolare alla meta della finistra in cui è scaduta l RTO)

- Riceve 3 ACK duplicati: alla destinazione cio che mando arriva MA arriva fuori ordine. C'è una congestione ma non è una situazione grave
con $W_C = k$ appena ricevo 3 ACK duplicati, dimezzo la finestra e riprendo ad aumentare la finestra in modo lineare

3 ACK potrebbero essere molti
La sorgente una volta capito di aver ricevuto le cose non in ordine, puo utilizzare un SACK (SelectiveACK) per specificare il segmento che ho ricevuto insieme al ACK che rappresenta invece quello che mi aspettavo


Explicit Congestion Notification
SE sappiamo che i buffer si stanno riempendo e si sta per causare una congestione, i router protrebberlo notificarlo in modo da far diminuire le finestre 

A livello IP, ci sono 2 bit che se settati a 11, vuol dire che è stato sperimentata una congestione (i router devono pero essere abilitati a gestire ECN)
Poi verra gestita dai router che non cambieranno questa informazione in modo che arriva alle destinazioni
Il router marca quindi ECE (ECN Echo) a 1 in modo che tutti gli ACK che manda lo avranno in modo da notificare il router

Le primitive IP informano il TCP riducendo cosi la finestra nelle destinazioni
Il bit CWR (CongestionWindowReduced) viene quindi settato a 1 nei successivi segmenti in modo che la destinazione informi i router di aver ridotto la finestra
