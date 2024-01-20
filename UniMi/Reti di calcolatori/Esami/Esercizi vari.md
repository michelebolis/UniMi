- Determinare massimo ritardo di propagazione associato con i seguenti canali di comunicazione: 
1. connessione attraverso linea telefonica di 1 Km  
2. connessione via canale satellitare di 50000 Km 

Nel primo caso il mezzo è in rame, perciò $v_p = 2*10^8m/s$; 
nel secondo caso è $v_p = 3*10^8m/s$. 
Perciò: 
1. $t_p = \frac {10^3 m}{2*10^8m/s} = 0.5*10^{-5} s$.  
2. $t_p = \frac {5*10^7 m} {3*10^8m/s} = 1.67 * 10^{-1} s$.

- Se data link layer usa bit stuffing e preambolo di frame è 01110, mostrare quale sequenza di bit è trasmessa a partire dai dati 0 1 1 1 0 0 1 0 1 1 1 1 1 1
01110 011*0*1001011*0*11*0*11*0* 01110 

- Un canale ha bit rate 4 Kbps e ritardo di propagazione di 20 msec. Per quale range di frame size Idle RQ ha efficienza almeno 50%?

$U >=50$ SE $\frac {t_x}{t_x+2t_p} = \frac {{x}/{b}}{{x}/{b} + 2t_p} = \frac {x}{x+2bt_p}>=0.5$ 
$0.5x >=bt_p$
$x >= 2·b·t_p = 8000*t_p = 8000*0.02 = 160 bit$

- Calcolare l'utilizzo di un canale avente banda di 6 Mbps e lunghezza del cavo in rame di 4 Km, ottenuto da un protocollo di livello Data Link che genera frame di taglia fissata 1.5 Kb e che adotta un approccio di tipo stop-and-wait (Idle RQ).

$t_p = \frac {4*10^3}{2*10^8} = 2*10^{-5}$
$t_x = \frac{1.5*10^3}{6*10^6} = 0.25*10^{-3}$
$U = \frac {0.25*10^{-3}}{0.25*10^{-3} + 4*10^{-5}}=\frac {1}{16*10^{-2}}$

- Un blocco di dati da 3 Kb deve essere trasmesso tra due calcolatori connessi da un canale di comunicazione in rame lungo 70 Km e avente banda di 60 Mbps. Calcolare l'utilizzo del canale se il livello data-link usa un protocollo Go-Back-N con numeri di sequenza rappresentati con 3 bit.

$t_x = \frac {3*10^3}{60*10^6} = 1/2 * 10^{-4}$
$t_p = \frac{7*10^4}{2*10^{-8}} = 7/2 * 10^{-4}$
$U = \frac{k * t_x}{t_x+2t_p} = \frac{k/2 * 10^{-4}}{1/2 * 10^{-4} + 7 * 10^{-4}} = \frac {k10^{-4}}{8*10^{-4}} = k/16$
con 3 bit ho MxSeq = $2^3 -1$ = 7
$U = 7/16$

- Quali pacchetti in piu vengono mandati in un LS? 

Deve essere inviato anche un ACK e per ogni nodo faccio fludding

- Quali informazioni sono presenti in un LS e NON in un DV? 

Nel LS è presente anche la conoscenza della topologia della rete grazie al fludding

- Dovendo scegliere tra uno schema GoBackN e uno Selective Repeat quali elementi considero? 

Considero la memoria lato ricezione del buffer e preferisco Selective Repeat quando ho un collegamento instabile (Parametri: Memoria disponibile e canale affidabile)

- ARP: come ci si comporta nel caso la macchina destinazione NON appartiene alla stessa rete di quella sorgente? 

Sara necessario un proxy ARP il quale essendo collegato alla LAN riceve il broadcast ed essendo di livello 3 capisce che la destinazione è in un altra rete (grazie al NetID) propagando la ARPrequest e risolvendo il problema facendo una reply con il proprio MAC

- Un blocco di dati da 4 Kb deve essere trasmesso tra due calcolatori connessi da un canale di comunicazione in fibra lungo 50 Km e avente banda di 250 Mbps. Calcolare l'utilizzo del canale se il livello data-link usa un protocollo Selective Repeat con numeri di sequenza rappresentati con 4 bit.

$t_x = \frac {4*10^3}{25*10^7} = 0.16 * 10^{-4}$
$t_p = \frac {5*10^4}{3*10^8} = 5/3*10^{-4}$
$U = \frac {k0.16 * 10^{-4}}{0.16 * 10^{-4} + 10/3 * 10^{-4}} = k6/131$
Con 4 bit di sequence e utilizzando Selective Repeate, ho un $MxSeq = 2^4/2 = 8$
$U = 8*6/131 =0.37$ 

- Si consideri una rete con tratte di lunghezza massima 120 mt., dove si possono inserire al massimo due ripetitori consecutivi tra due dispositivi, con ritardo introdotto dai ripetitori 40 sec, banda dei canali 8 Mbps e mezzo in rame. In tale rete si vuole usare CSMA/CD; determinare la minima taglia di frame necessaria

Massima distanza $= 120 * 3 = 360m$
$t_p = 360/2*10^8 = 1.8 * 10^{-6}$
$t_p + 40*2 = 81.8  * 10^{-6}$
$t_x = \frac {x}{8*10^6} >= 163.6 * 10^{-6}$
$x >= 163.6 * 10^{-6} * 10^6 * 8$
$x >= 1309 bit$

- Qual è la minima dimensione di frame per una rete CSMA/CD con bwth 1 Gbps su un cavo di 1 Km senza ripetitori, tale che la velocità di propagazione è 2/3 della velocità della luce?

$t_p = \frac {10^3} {2 * 10^8} = 5*10^{-6}$
$t_x = \frac {x}{10^9} >= 10^{-5}$
$x >= 10^4$
$x >= 10kbit$

- Una stazione connessa ad una rete Ethernet subisce 5 collisioni consecutive nel tentativo di spedire un frame. In quale range temporale avverrà la successiva ritrasmissione secondo l'algoritmo BEB ?

$[0 - 2^5-1]*UT = [0-31]*UT$
con $UT = 51.2\mu s$, $[0 - 1587.2 \mu s]$

- Si supponga che un IP access gateway debba instradare su una LAN Ethernet tre pacchetti provenienti da una LAN in una rete non IP, contenenti rispettivamente 2875, 3862 e 1877 B di dati. Quanti frame Ethernet vengono generati, e qual è il loro contenuto di dati?

2875 = 1480 dati + 20 header | 1395 dati + 20 header
3862 = 1480 dati + 20 header | 1480 dati + 20 header | 902 dati + 20 header
1877 = 1480 dati + 20 header | 397 dati + 20 header

- Il protocollo TCP consegna al protocollo IP un segmento di 3720 byte da trasferire. Considerando che il pacchetto risultante dovrà essere trasmesso attraverso una tratta di sottorete Ethernet, indicare il contenuto dei campi fragment offset e total length dei frammenti generati e specificare il numero di byte contenuto nel payload

MSS = 1480

| Segmento | Data | Fragment offset | Total length | MID |
| ---- | ---- | ---- | ---- | ---- |
| S1 | 1480 | 0 | 3720 | 1 |
| S2 | 1480 | 185 | 3720 | 1 |
| S3 | 760 | 370 | 3720 | 0 |

- Si considerino gli effetti dell’uso di slow start su una linea con RTT di 10 msec. e nessuna congestione. La finestra di ricezione è 24 KB e la massima dimensione di segmento è 2 KB. Quanto tempo è necessario prima che possa essere inviata una finestra intera, se la slow start threshold è 32 KB?

Supponendo che non scada mai l RTO, A t=0 invio 2KB, a t=10msec invio 4KB, t=20msec invio 8KB, t=30msec invio 16KB quindi a t=40msec raggiungo la $W_C = 32KB$ MA dovro fare il min con la finestra di ricezione
(NOTA che si raddoppiano perche mando a t=10msec 4 segmenti e ricevo 4 ack quindi aumento di 4 la finestra raddoppiandola)

- Si supponga che la finestra di congestione di TCP sia di 18 KB nel momento in cui si verifica un retransmission timeout. Quando sarà grande la finestra se le successive 4 trasmissioni avvengono con successo? Si assuma che la max dimensione di segmento sia 1 KB e la slow start threshold sia di 16KB.

t= 0, RTO expires -> $W_C = 1KB$, $SST = 18/2 = 9KB$
t=1, $W_C = 2KB$
t=2, $W_C = 3KB$
t=3, $W_C = 4KB$
t=4, $W_C = 5KB$

- Una connessione TCP che adotta l’algoritmo di Clark ha dimensione di receiver window 3800B e MSS 1200B. Se a lato receiver c’è un’applicazione interattiva che consuma 1B ogni 40 msec., e a lato sender c’è sempre disponibilità di dati da spedire, dire ogni quanto il receiver invia un window update, assumendo che i ritardi di propagazione siano trascurabili.

3800/2 = 1900B
min(1900, 1200) = 1200B
A buffer pieno si aspetta che di avere 1200B liberi prima di mandare il window update
$1200*40msec = 48000msec$

- Si supponga che la finestra di congestione di TCP sia di 18KB quando si verifica l’arrivo di 3 duplicate ack. Si assuma che la MSS sia 1 KB e la SST sia 16KB. Quali sono i due nuovi valori di SST e Congestion Window? Quanto sarà grande la finestra se alle successive 2 trasmissioni (oltre alla ritrasmissione) corrisponde l’arrivo di duplicate ack? Cosa succede se dopo la 3° trasmissione si riceve un altro duplicate ack?

$SST = 18/2 = 9KB$
$W_C  = 18/ 2 = 9KB$
nelle due successive 2 trasmissioni la finestra resta a 9KB ma all arrivo del terzo ACK duplicato:
SST = 9/2 = 4.5KB
W_C = 4.5KB

- Se il RTT di TCP è correntemente 30 msec., RTO è 38 msec. e i successivi ack arrivano dopo 26 msec. e 32 msec. dalle rispettive trasmissioni, quali sono le nuove stime di RTT e RTO usando a=0.9?

$RTO = RTT + 4RTTVAR$
$38 = 30 + 4RTTVAR$
$8 = 4RTTVAR$
$RTTVAR = 2$

Trasmissione 1
$RTTVAR = 0.9 * 2 + 0.1 * |30-26| = 2.2$
$RTT = 0.9 * 30 + 0.1 * 26 = 29.6$
$RTO = 29.6+4*2.2 = 38.4$

Trasmissione 2
$RTTVAR = 0.9 * 2.2 + 0.1 * | 29.6 - 32| = 2.22$
$RTT = 0.9 * 29.6 + 0.1 * 32 = 29.84$
$RTO = 29.84+4*2.22 = 38.72$

- Una connessione TCP ha RTT=27 msec. e RTO = 35 msec. Quando si verifica unretransmission timeout. Indicare quali sono i valori di RTT e RTO:
i. usati per la ritrasmissione con successo che produce misura M=43 msec.

RTT non viene aggiornato secondo Karn e RTO viene raddoppiato a 70msec

ii. usati per la trasmissione del segmento successivo (con successo)

RTT non viene aggiornato secondo Karn e RTO viene raddoppiato a 70msec

iii. considerati dopo la ricezione dello ack per la trasmissione al punto (ii) con misura M=41
msec.

$RTTVAR = 41/2 = 20.5$
$RTT = M = 41$
$RTO = 41+4*20.5 = 123$

- Si consideri una connessione TCP con applicazione interattiva a lato sender che produce 1B di dati ogni 20 msec., e con link avente banda di 100 Kbps e tempo di propagazione di 100 msec. Dire quali sono le dimensioni dei primi 3 segmenti inviati sulla connessione, se TCP adotta l’algoritmo di Nagle.

Primo segmento 1B+20B = 21B
$t_x = \frac{21*8}{100000} = 1.68*10^{-3}$
$t_p= 100msec$
ack arriva dopo $1.68+2* 100 = 201.68msec$
In questo tempo sono stati prodotti $201.68/20 = 10$ B

Secondo segmento: 10B+20B = 30B
$t_x = \frac {30*8}{100000} = 2.4*10^{-3}$
ack arriva dopo $2.4 + 2*100 = 202.4msec$
In questo tempo sono stati prodotti $202.4/20 = 10B$

Terzo segmento (e tutti i successivi): 10B+20B = 30B