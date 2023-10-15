Approccio "casuale"


Su reti distribuite il controllo deve essere totalmente distribuito

Tecnologie dominante nelle reti locali
Non esiste nessuna funzione di accesso che sia concentrata su una stazione.
Ogni stazione è in grado di operare in autonomia: ciò implica un accesso immediato in qualsiasi momento di un qualsiasi nuovo dispositivo

Ethernet introduce un controllo di accesso probabilistico
Una stazione A invia il suo messaggio: riesce a trasmettere quando è l'unico a tentare l'accesso al canale in quell'istante. SE nello stesso istante due stazioni tentano l accesso, i due messaggi collidono 
Per rilevare la collisione le stazioni fanno complemento bit a bit di ciò che inviano e ciò che ricevono, sospendendo la trasmissione 

Questo era il protocollo ALOHA

SE il numero di stazioni è basso, le collisioni saranno in numero minore 
Risultato di efficienza: la curva di ALOHA ha una forma di campana in quanto all'aumentare delle stazioni ho un utilizzo maggiore ma fino a un certo punto in cui ci sono troppe stazioni che causano collisioni. Il picco della curva è del 18%

Il "vero" protocollo Ethernet 
A vuole trasmettere, prima di farlo fa Carrier Sense: legge dal canale ciò che passa, capendo se è il canale è in idle o meno.
Le collisioni ci sono quando SE B sta trasmettendo e C fa CS, quindi aspetta 1-persistent aspettando che B finisca MA se un 2o nodo fa CS, ora entrambi stanno aspettando la terminazione di comunicazione di B e entrambi faranno CS nello stesso momento

Ha sempre una forma a campana la curva di utilizzo ma il punto di saturazione ora è al 91%

SE applicassimo la stessa tecnica di ritrasmissione della finestra, avremmo nuovamente una collisione 

La probabilita di collisione è tanto maggiore tanto piu stazioni ci sono sul canale 

Soluzione: protocollo CSMA-CD Carrier Sense Multiple Access - Collision Detection (standardizzato come IEEE 802.3, es Wi-Fi IEEE 802.11)
Ritrasmissione dei frame coinvolti nella collisione facendo aspettare le stazioni coinvolte un tempo tau casuale. 
La generazione del numero casuale non ha un range ampio, tecnica 
$Binary$ $Exponenzial$ $Backoff$ $(BEB) = [0:2^i]*UT$ con i il numero di collisioni (1<i<16) della stazione e UT unita di tempo 

Potrebbero ancora collidere se viene generato lo stesso numero di UT ma è probabilistico
In condizioni ottimali il protocollo lavoro intorno al 90% di utilizzo

E' un controllo completamente distribuito

La fairness è smussata qui perche se A deve trasmettere molti frame va in collisioni con le altre stazioni non potendo trasmettere


provando tutti i gradi di persistenza...: non persistente tanto che appena rilevo CS, genero subito un numero casuale in cui non controllo il CS


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
Il L2 di Ethernet è multi-layer, in particolare 2:
- MAC Media Access Control: funzionalità di Carrier Sense, BEB, Collision Control
- LLC Logical Link Control: protocollo a finestra affidabile o meno 