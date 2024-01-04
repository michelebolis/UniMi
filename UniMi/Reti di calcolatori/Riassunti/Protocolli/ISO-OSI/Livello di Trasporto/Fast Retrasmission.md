Manteniamo una variabile sia nel mittente che nel destinatario ($V_S$/$V_R$) con la Initial Sequence number 
Assumiamo ACK immediato, che quando arriva alla sorgente questa aggiorna il proprio Vs con X+500
Mandando un secondo messaggio, questo viene perso MA ho trasmesso un terzo messaggio che è arrivato alla destinazione.
Il SEQ è diverso da quello che si aspetta il ricevente, quindi lo conservo nel buffer di TCP SENZA passarlo al buffer dell'applicazione
MA non posso rispondere con un ACK X+1000, quindi rispondo con un ACK X+500 perche è quello che mi aspetto
Lato mittente, si aspettava un X+1500, MA non glielo rinvio subito in quanto potrebbe arrivare in ritardo alla destinazione. Nel caso non arrivi pero, viene ignorato il problema e vengono inviati altri segmenti SENZA togliere pero dal buffer il 2o e 3o dal buffer perche non sono arrivati in ordine. Se altri messaggi arrivano al ricevente, verra inviato lo stesso ACK errato precedente, quindi viene ritrasmesso il segmento X+500 (Fast Retrasmission) che stavolta arriva al ricevente
Il ricevente ha quindi nel buffer i segmenti in "ordine", mandando un ACK cumulativo. La sorgente quando riceve l ACK cumulativo, ripulisce il proprio buffer 

TCP ritrasmette un segmento SOLO quando riceve 3 ACK duplicati per lo stesso segmento
Questo sistema funziona finche ho qualcosa da trasmettere, difatti non verra mai mandato un ACK al mittente. 
Per ogni trasmissione, un RTO inizia per il nuovo segmento 
Quando la ritrasmissione avviene prima dello scadere dell RTO, in quanto ho ricevuto 3 ACK duplicati, si parla di Fast Retrasmission

[[Calibrazione RTO]]