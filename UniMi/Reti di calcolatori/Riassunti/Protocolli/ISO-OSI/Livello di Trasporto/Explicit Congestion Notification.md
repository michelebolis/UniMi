SE sappiamo che i buffer si stanno riempendo e si sta per causare una congestione, i router potrebbero notificarlo in modo da far diminuire le finestre 

A livello IP, ci sono 2 bit che se settati a 11, vuol dire che è stato sperimentata una congestione (i router devono pero essere abilitati a gestire ECN)
Poi verra gestita dai router che non cambieranno questa informazione in modo che arriva alle destinazioni
Il router marca quindi ECE (ECN Echo) a 1 in modo che tutti gli ACK che manda lo avranno in modo da notificare il router

Le primitive IP informano il TCP riducendo cosi la finestra nelle destinazioni
Il flag CWR (CongestionWindowReduced) viene quindi settato a 1 nei successivi segmenti in modo che la destinazione informi i router di aver ridotto la finestra