Approccio "casuale"

Su reti distribuite il controllo deve essere totalmente distribuito: non esiste nessuna funzione di accesso che sia concentrata su una stazione.
Ogni stazione è in grado di operare in autonomia: ciò implica un accesso immediato in qualsiasi momento di un qualsiasi nuovo dispositivo

Ethernet introduce un controllo di accesso probabilistico
- Protocollo ALOHA:
Una stazione A invia il suo messaggio: riesce a trasmettere quando è l'unico a tentare l'accesso al canale in quell'istante. SE nello stesso istante due stazioni tentano l'accesso, i due messaggi collidono 
Per rilevare la collisione le stazioni fanno complemento bit a bit di ciò che inviano e ciò che ricevono, sospendendo la trasmissione 

Risultato di efficienza: la curva di ALOHA ha una forma di campana in quanto all'aumentare delle stazioni ho un utilizzo maggiore ma fino a un certo punto in cui ci sono troppe stazioni che causano collisioni. Il picco della curva è del 18%

- Protocollo Ethernet
A vuole trasmettere, prima di farlo fa $Carrier Sense$: legge dal canale ciò che passa, capendo se è il canale è in idle o meno.
Le collisioni ci sono quando SE B sta trasmettendo e C fa CS, quindi aspetta 1-persistent aspettando che B finisca MA se un nodo fa CS, ora entrambi stanno aspettando la terminazione di comunicazione di B e entrambi faranno CS nello stesso momento

La curva di utilizzo ha sempre una forma a campana ma il punto di saturazione ora è al 91%

SE applicassimo la stessa tecnica di ritrasmissione della finestra, avremmo nuovamente una collisione 

La probabilità di collisione è tanto maggiore tanto piu stazioni ci sono sul canale 

Soluzione: 
Protocollo CSMA-CD Carrier Sense Multiple Access - Collision Detection 
Standardizzato come IEEE 802.3 (es Wi-Fi IEEE 802.11)
Ritrasmissione dei frame coinvolti nella collisione facendo aspettare le stazioni coinvolte un tempo $\tau$ casuale. 
La generazione del numero casuale non ha un range ampio, tecnica 
$Binary$ $Exponenzial$ $Backoff$ $(BEB) = [0:2^i-1]*UT$ con i il numero di collisioni (1<i<16) della stazione e UT unita di tempo 

Potrebbero ancora collidere se viene generato lo stesso numero di UT ma è probabilistico
In condizioni ottimali il protocollo lavoro intorno al 90% di utilizzo

E' un controllo completamente distribuito

La fairness è smussata qui perche se A deve trasmettere molti frame va in collisioni con le altre stazioni non potendo trasmettere



Problema del tempo di propagazione
A trasmette ma il CD arriva dopo $T_p$ a B che non vedendo il canale occupato, aveva iniziato a trasmettere cosi A, dopo aver finito di trasmettere, riceve dopo $T_p$ il frame corrotto di B
A non è in grado di rilevare la collisione 
CD quindi non funziona sempre --> sistema inaffidabile

Soluzione: 
lavorare sul $T_x$
Imporre di usare la propria porta di I/O di trasmissione almeno pari a $2 * T_p$
$T_x \geq 2 * T_p$
A cosi sta ancora trasmettendo quando arriva il messaggio corrotto, rilevando cosi la collisione 

La lunghezza del cavo di Ethernet è 2500mt a 10Mbps
${25*10^2 \over 2*10^8}$ = 12,5 micro secondi
$2 * T_p$ = 25 micro secondi
L'ente standardizzatore lo ha fatto diventare 51.2 micro secondi
Al massimo produce 512 bit -> 64 Byte 
Al minimo ogni frame ha 64 Byte 

Dimensione di frame per lo standard Ethernet è 

SE una rete LAN deve essere maggiore di piu di 2.5km, ne creo un altra e le compongo

MA in BEB UT = 51,2 micro secondi


La stazione di rete Ethernet ha come tutte un L1 attaccato al cavo, con un clock, un codificatore di bit


sempre livello 2 topologie broadcast
il protocollo ci dice che il cavo puo essere max 2.5 km, ci possano essere al massimo 4 repeater 
c è uno slot di contesa $T_x$ >= $2*T_p$
Per il protocollo CSMA-CD la collisione è un evento possibile

ogni stazione ha un contatore per generare il numero casuale, in particolare per l'indice i 

Quanto BEB incide sulle prestazioni: l'algoritmo dilata l'accesso NON garantendo la fairness
è pero un algoritmo adattivo al traffico percepito, in quanto dipende dal numero di collisioni i
OSS ogni stazione NON sa quante stazioni sono in contesa 

Osservando $$U = {t_x \over t_x+2t_p * {1 \over A}}$$
$1 \over A$ = Numero medio di stazioni che deve aspettare prima di accedere
$A= k*p * (1-p)^{kp}$
k numero di stazioni
p probabilita che quella stazione possa accedere al canale 

come min devo avere 64byte, e con DA, SA, L e CRC ho solo 18 byte
Ho quindi un campo padding per arrivare ai 64byte: parte da 0 a 46 byte

Pero come min il livello 3 mette un header di 20byte, quindi avremmo gia 38byte

L ci dice quanto è lungo il payload, indicando quindi anche di quanto è il PAD
Payload+PAD deve essere <= 1500 Byte (con rete a 10Mbps)


Problema: 3 stazioni su un cavo condiviso in contesa
A invia e B e C ricevono
B e C ricevono in modo asincrono ma è difficile da realizzare in quanto B e C devono attivare il clock di ricezione, dovendo quindi essere sincronizzato con quello del mittente MA non è dato sapere quando A trasmette

In banda base, SE trasmetto 3 1, il segnale rimane alto
In Ethernet invece i 3 1, viene garantito una transizione di stato da 1 a 0: codifica di Manchester


Oggi la gran parte delle reti Ethernet è fatta con questa topologia

il protocollo specifica anche il clock