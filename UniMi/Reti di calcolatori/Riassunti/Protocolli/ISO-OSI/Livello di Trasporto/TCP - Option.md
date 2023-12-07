Le opzioni sono multipli interi di 32 bit nell header TCP
- MSSO - Max Segment Size Option
	- Campo che identifica l opzione es Kind=2 -> Max Segment Size Option
	- Campo che identifica la lunghezza in byte es lenght = 4 
	- Option

- Window scale 
Inefficienza SE banda/RTT alta, posso mandare molti dati, molti piu dei 16 byte della window size
Window scale option: kind = 1, Kind = 3, Length = 3, Shift count
Kind = 1 è una NOT Option per fare padding e raggiungere i 32 byte
Lo shift count = 0 SE non viene fatto uno scaling
è = 1 SE multiplico per 2^1
...


- Time stamp option: deve essere abilitata durante l apertura della connessione
Kind = 1, Kind = 1, Kind = 8, Length = 10
Time stamp value (quando è stato inviato il segmento dalla sorgente)
Time stamp echo reply 

Serve nei casi in cui la finestra sia abbastanza grande e quindi la stima dell RTT deve essere precisa
SE pensiamo ad una sorgente che manda quasi instantaneamente N messaggi ma questi non arrivano insieme alla destinazione ma dilatati. SE mando un ACK cumulativo sto in realta sovrastimando a causa dell ultimo segmento

Con i timestamp invece, quando ricevo il primo segmento dopo un ACK, salvo il timestamp in TSRecent e cosi nell ACK cumulativo usero TSE = TSRecent. 
Nella sorgente al tempo t3 stima RTT = t3-FirstTS (e quindi non t3-t2)
