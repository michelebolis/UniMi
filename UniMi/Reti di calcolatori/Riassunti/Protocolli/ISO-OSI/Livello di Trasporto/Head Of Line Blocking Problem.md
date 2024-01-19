Immaginiamo di avere 3 messaggi che, essendo visti come un unico byte stream, quest'ultimo viene segmentato a prescindere da cosa sia contenuto nei segmenti ottenuti
es 
Segmento 3: M3 | M2
Segmento 2: M2 | M1
Segmento 1: M1

SE viene perso $S2$, alla ricezione se riceve $S3$, il TCP non puo mandare l'ACK MA dal punto di vista dell'applicazione in S3 ci sarebbe tutto il messaggio 3 in quanto indipendente dal Segmento 2