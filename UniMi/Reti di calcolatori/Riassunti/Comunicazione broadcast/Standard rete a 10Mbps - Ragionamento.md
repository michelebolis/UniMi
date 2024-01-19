1. Lunghezza massima del cavo: `2.5km`: SE una rete LAN deve essere maggiore di piu di 2.5km, ne creo un altra e le compongo
2. $t_x$ minimo: $51.2\mu s$

Problema:
Stazione $A$ trasmette ma il CS arriva dopo $t_p$ alla stazione B che, non vedendo il canale occupato, aveva iniziato a trasmettere cosi $A$, dopo aver finito di trasmettere, riceve dopo $t_p$ il frame corrotto di B
$A$ non è in grado di rilevare la collisione 
![[photo_5769355704325488864_y.jpg|400]]

Soluzione: 
Imporre di usare la propria porta di I/O di trasmissione almeno per $2 * T_p$
$$T_x \geq 2 * T_p$$
$A$ cosi sta ancora trasmettendo quando arriva il messaggio corrotto, rilevando cosi la collisione 

${25*10^2m \over 2*10^8} = 12.5 * 10^{-6}m/s = 12.5 \mu s$
$2 * T_p = 25 \mu s$
L'ente standardizzatore lo ha fatto diventare $51.2 \mu s$
Da ciò deriva che l'UT utilizzato nel BEB è di $51.2 \mu s$

3. Size minima del frame: 64Byte

Al massimo produce $512 bit -> 64 Byte$
Come min devo avere $64byte$, MA con DestinationA, SourceA, L e CRC ho solo 18 byte
Ho quindi un campo padding per arrivare ai 64byte: parte da 0 a 46 byte

Pero come min il livello 3 mette un header di 20byte, quindi avremmo gia 38byte