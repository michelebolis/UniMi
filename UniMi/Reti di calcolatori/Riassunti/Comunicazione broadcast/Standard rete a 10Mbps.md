- Lunghezza massima del cavo: 2.5km
SE una rete LAN deve essere maggiore di piu di 2.5km, ne creo un altra e le compongo

- $T_x$ minimo: 51.2 ms

A trasmette ma il CD arriva dopo $T_p$ a B che non vedendo il canale occupato, aveva iniziato a trasmettere cosi A, dopo aver finito di trasmettere, riceve dopo $T_p$ il frame corrotto di B
A non è in grado di rilevare la collisione 

Soluzione: 
lavorare sul $T_x$, imporre di usare la propria porta di I/O di trasmissione almeno pari a $2 * T_p$
$T_x \geq 2 * T_p$
A cosi sta ancora trasmettendo quando arriva il messaggio corrotto, rilevando cosi la collisione 

${25*10^2 \over 2*10^8}$ = 12,5 ms
$2 * T_p$ = 25 ms
L'ente standardizzatore lo ha fatto diventare 51.2 micro secondi

- Size minima del frame: 64Byte
Al massimo produce 512 bit -> 64 Byte 
Al minimo ogni frame ha 64 Byte 

Da ciò deriva che l'UT utilizzato nel BEB è di 51,2 ms

- Padding
Ogni stazione ha un contatore per generare il numero casuale, in particolare per l'indice i 

Quanto BEB incide sulle prestazioni: l'algoritmo dilata l'accesso NON garantendo la fairness
è pero un algoritmo adattivo al traffico percepito, in quanto dipende dal numero di collisioni i

Osservando $$U = {t_x \over t_x+2t_p * {1 \over A}}$$
Con: 
- $1 \over A$ = Numero medio di stazioni che deve aspettare prima di accedere
- $A= k*p * (1-p)^{kp}$
- k numero di stazioni
- p probabilita che quella stazione possa accedere al canale 

Come min devo avere 64byte, MA con DA, SA, L e CRC ho solo 18 byte
Ho quindi un campo padding per arrivare ai 64byte: parte da 0 a 46 byte

Pero come min il livello 3 mette un header di 20byte, quindi avremmo gia 38byte

- Payload+PAD deve essere <= 1500 Byte (con rete a 10Mbps)