Formato: Kind = 1 | Kind = 1 | Kind = 8 | Length = 10
Ad ogni invio di dati, il TCP legge il current time e scrive nel campo `time stamp value` e quando il TCP restituisce un ACK, scrive il time stamp nel `time stamp echo reply`

Serve nei casi in cui la finestra sia abbastanza grande e quindi la stima dell'RTT deve essere piu accurata
SE pensiamo ad una sorgente che manda quasi istantaneamente N messaggi ma questi non arrivano insieme alla destinazione ma dilatati. SE mando un ACK cumulativo sto in realta sovrastimando a causa dell ultimo segmento

Con i timestamp invece, quando ricevo il primo segmento dopo un ACK, salvo il timestamp in TSRecent e cosi nell'ACK cumulativo usero TSE = TSRecent. 
Nella sorgente al tempo t3 stima RTT = t3-FirstTS (e quindi non t3-t2)