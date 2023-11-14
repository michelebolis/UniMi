CAP 1
Modalità di comunicazione
- Simplex: i dati fluiscono in un'unica direzione
- half-duplex: i dati fluiscoon in entrambe le direzione MA in modo alternato
- duplex: i dati fluiscono in entrambe le direazioni contemporaneamente 
- broadcast: i dati vengono inviati da un singolo device a TUTTI gli altri device
- multicast: i dati vengono ricevuto da tutti i device di un sottoinsieme connessi alla rete

...

La somma dei delay degli store and forward contribuisce al delay di trasferimento del pacchetto, jitter,  attraverso la rete


Netword Quality Of Service
La maggior parte delle rete mette a disposizione:
- Servizio non affidabile o best-try / best-efford
- Servizio affidabile: che permesse l'invio di un blocco mancate del pacchetto, portando pero ad un overhead necessario nei pacchetti

Per risolvere il problema del jitter, si usa la tecnica di buffering che permette di mantenere un certo numero di pacchetti in una memoria bufferizzati alla destinazione 

QoS sono definiti mediante classi di servizi a cui viene assegnata una relativa priorità


Digital communication
In ogni sistema finale vi è una NIC network interface card, un HW controllato dal relativo SW che esegue le funzioni di rete

Le linee di accesso usano tutte una trasmissione seriale bit a bit.
Il segnale in output dalla NIC varia tra due livello di voltaggio \[-V; +V], secondo un bit rate
Questa è la trasmissione in banda base

Le reti LAN usano la trasmissione in banda base

Quando si trasmette ogni tipo di segnale elettrico su una linea di trasmissione, il segnale è attenuato e distorto dal mezzo trasmissivo. Inoltre è sempre presente del rumore.


Mezzi trasmissivo
- Twisted-pair
E' composta da una coppia di cavi attorcigliati insieme in modo tale da ridurre le interferenze.
E' possibile avere piu coppie nello stesso cavo, per ridurre ulteriormente rumori.
- UTP unshilded Twisted Pairs sono usato nella rete telefonica e in molte reti locali
- STP Shilded Twisted Pairs sono avvolti da uno schemo/scudo usato per ridurre le interferenze
Limite: la capacità elettrica

- Coaxial cable
I due cavi sono come un centro solido conduttivo dentro a un ...

- Fibra ottica
Nei cavi di fibra ottima il bitstream viene trasmesso sotto forma di luce in un cavo di vetro grazie a un LED o un laser diodo e ricevuto con photo trasistor o un photo diodo
Vantaggi: riesce a raggiungere velocità di centinaia di Mbps e la luce è immune alle interferenze elettromagnetiche


Tempo di propagazione
Per propagare un segnale elettrico da un punto a un altro vi è sempre un tempo finito necessario, il tempo di propagazione
Il round-trip delay invece è il tempo tra il momento in cui il primo bit viene trasmesso, al momento in cui l ultimo bit di ACK viene ricevuto


Manchester encoding: estrazione e codifica del clock
Ogni bit è codificato come basso-alto (1) o alto-basso (0), prevedendo quindi sempre una transazione, che avviene al centro di un ogni "cella" del bit
Il segnale di clock si ottiene shifatando di mezzo bit cell dal centro


Error control
Il ricevente controlla il frame per dei possibili errori di trasmissione, ritornando un segnale di ACK positivo o negativo (NACK) in modo da richiedere nuovamente il frame
Questo tipo di controllo dell'errore viene detto Automatic Repeat Request ARQ

Tipi di ARQ
- Idle RQ
Questo schema viene anche chiamato send-and-wait o stop-and-wait
Opera in una modalità half-duplex

Il mittente invia solo un I-frame alla volta, facendo partire un timer ogni volta che ne invia uno.
- Il ricevente informa il mittente della corretta ricezione del frame con un acknowledgment o ACK-frame, in modo che il mittente resetti il timer e invii il successivo.
- SE l'I-frame contiene degli errori, viene inviato un negative acknowledgment o NAK-frame, in modo che il mittente proceda ad inviarne un altra copia, restartando il timer.
- SE invece P non riceve l'ACK entro lo scadere del timer, P ritrasmette l'I-frame di cui stava aspettando l'ACK. Il destinatario riconosce che il frame ricevuto è un duplicato e provvede a scartarlo e a mandare l'ACK del frame.

Per fare in modo che il destinatario determini che il frame ricevuto sia o meno un duplicato, ogni frame contiene un identificativo numerico di sequenza come anche ogni ACK associato all'i-esimo frame

Il tempo minimo a cui il timer deve essere settato, quindi il tempo prima di inviare il prossimo frame, è approssimativamente Tx+2Tp

- Continuous RQ
Opera in modalità duplex

Il mittente invia I-frame in modo continuativo senza aspettare il ritorno di un ACK. Il mittente conserverà quindi una copia dell'I-frame trasmesso in un lista di ritrasmissione. 
Il destinatario anche in questo caso invierà un ACK per ogni frame ricevuto correttamente, conservandolo in una lista di ricezione. Anche in questo caso sarà necessario avere nei frame e negli ACK un numero di sequenza identificativo
Alla ricezione del ACK, viene rimosso dalla lista il corrispettivo frame

Il mittente conserva una variabile di sequenza N(S) che indica il prossimo frame da trasmettere
Il destinatario invece conserva una variabile di sequenza V(R) che indica il prossimo frame che sta aspettando

Strategie di ritrasmissione: 
- Selective repeat 
Assumendo che l'I-frame N+1 sia corrotto e che il destinatario abbia mandato un ACK per il frame N. Quando il destinatario riceve il frame N+2, grazie a V(R) riconosce che manca il frame N+1, inviando quindi un NAK-N+1, bloccando l'invio di nuovi ACK.
Il mittente quindi invia nuovamentre N+1, sospendendo la trasmissione di nuovi frame e settando un timer per la ricezione dell'ACK-N+1.
Una volta ricevuto il frame N+1, il destinatario riprende a inviare ACK MA non poi invierà un ACK superiore a N+1 in quanto nella sua lista di ricezione aveva già ricevuto dei frame corretti

Assumendo che l'ACK-N sia corrotto, il mittente ritrasmette il frame N ma il ricevente, grazie a V(R), lo identifica come un duplicato, scartandolo e inviando ACK-N

- Go-back N
Assumendo che l'I-frane N+1 sia corrotto e che il destinatario abbia ricevuto il frame N+2 fuori sequenza. Invia quindi al mittente un NAK-N+1, causando la sospensione dell invio di nuovi frame. 
Il destinatario scarta nuovi frame finchè non riceve l'N+1.

Assumendo che ACK-N e ACK-N+1 siano corrotto, il mittente alla ricezione dell'ACK-N+2, assume che siano i due ACK siano stati corrotti ma non li invia nuovamente in quanto ha ricevuto ACK di un frame successivo


Controllo di flusso
Controllare il flusso di frame viene utilizzato il meccanismo della sliding window.
Esso prevede di impostare un numero massimo di frame di cui posso aspettare un ACK, questo limite è detta finestra k.
SE k=1, stiamo usando un idle RQ

Idle RQ e go-back N necessitano solo di un buffer mentre per il selective repeat sono necessari k frame. 

Numero di identificatori:
- Idle RQ: le finestre di ricezione e invio sono entrambe 1.
- Go back N: data una finestra di K, il numero di identificatori deve essere di almeno k+1 in quanto con k usato, il ricevente non sarebbe in grado di determinare se il un frame ricevuto sia nuovo o il duplicato del precedente
- Selective repeat: data una finestra di k, il numero di identificato deve essere di almeno 2k, in quanto nel caso peggiore in cui vengano inviati k frame e tutti gli ACK siano corrotti, il destinatario deve essere in grado di determinare se uno dei successivo k frame sia un nuovo frame.


Ogni layer ha un serie di funzioni ben definite nel contesto del sottosistema di comunicazione
Viene aggiunto un protocol control information PCI all'head dei dati che devono essere trasmessi

TCP/IP protocol stack
- User interface
- Application layer: fornisce all'utente l'accesso a una serie di applicativi
- Transport layer: eroga servizi indipendenti dalla rete
	- TCP Transmission control protocol: eroga un servizio affidabile
	- UDP User Datagram Protocol: eroga un servizio best-efford
- Network layer: guida i dati attraverso la rete 
- Link layer: comprende due sublayer
	- Link control LC: riguarda l'implementazione del controllo degli errori e di flusso che sono usati indipendentemente dalla modalità di controllo della trasmissione
	- Medium accesso control MAC: riguarda la trasmissione di blocchi usando una modalità di controllo della trasmissione che puo variare a secondo della rete
- Il livello fisico comprende i circuiti per la codifica del clock e dei bit, i circuiti per la ricezione

CAP 2


CAP 3
Le LAN sono utilizzato per interconnettere insiemi di end sistem, stazioni
LAN standard serie IEEE 802

Le LAN Ethernet operano usando CSMA/CD, standard IEEE 802.3
Le LAN Token Ring operano usando il control token, standard IEEE 802.5


CSMA/CD
Dato che tutte le stazioni lavorano sullo stesso cavo/bus, si dice che operano in multiple  access MA mode
Il bus operano in broadcast in quanto ogni frame trasmesso è ricevuto da tutte le stazione connesse al bus

Una collissione si verifica quando due o piu stazioni provano a trasmettere un frame sul bus nello stesso tempo
Viene quindi introdotto il carrier sensed con cui la stazione, dopo aver rilevato una possibile collisione (collision detection CD), rimanda la sua trasmissione finche il frame corrente non è stato trasmesso, e solo poi prova a inviare il proprio 

Lo slot time serve ad assicurare che una stazione riesco a rilevare la collisione prima di inviare il suo frame
Dopo la rilevazione della collisione, viene  atteso un tempo randomico prima di ritrasmettere il proprio frame
La probabilita di collisione aumenta con l aumentare del traffico della rete 

Il processo di binary exponential backoff viene utilizzato per definire il tempo da attendere prima della ritrasmissione, che aumenta in modo esponenziale dopo ogni nuovo ritrasmissione
Il tempo da aspettare è da 0 a 2n - 1 UT

CSMA/CD NON garantisce che il frame che arriva senza collisioni sia senza errori

Formato dei dframe
Tutti i frame sono trasmessi usando la codifica di Manchester
Il SFD Start Of Frame Delimiter è composto da un singolo byte 10101011
L'indirizzo del destinatario e del mittente sono indirizzi MAC, che identificano l'interfaccia HW del destinatario e del mittente
Vi sono poi due byte dedicati alla lunghezza/type che indica la lunghezza del payload
SE questa lunghezza è minore del minimo richiesto per un frame valido, allora viene aggiunta una sequenza di byte, padding
La massima dimensione del payload è invece di 1500bytes
Infine FCS contiene un CRC value per rilevare l errore


Hub
Ripetono ogni frame ricevuto su ogni porta

Bridge
Tutti i frame ricevuto sono prima bufferizzati e poi ripetuto come nell'hub tranne dalla porta in cui è arrivato
Il bridge mantiene una forwarding database che indica, per ogni porta, la porta di uscita da utilizzare per mandare il frame a quella porta

Quando un bridge si avvia, la sua forwarding database è vuota.
Quando riceve un frame, legge quindi l'indirizzo della sorgente e aggiunta la entry alla sua tabella 
Invia quindi una copia del frame a tutte le altre porte
Ad ogni entry della tabella è associato un timer che le resetta periodicamente


Switch
Gli switch lavorano in duplex sui cavi
I frame ricevuti sono conservati in una coda FIFO

Il processo leggera l'header per ottenere il MAC address e trasmettere il frame alla coda di uscita corretta.
Ha un processo di apprendimento simile al bridge
In questo caso vi è un delay associato allo store-and-forward


Gigabit
Sono cavi che possono operare fino a 1000 Mbps
Inizialmente la lunghezza massima del cavo era stata proposta a 15 m ma poi era stata rigettata, optando per 200m.
La size minima del frame è stata invece standardizzata a 512 bytes (da 64bytes)

Quando un frame con meno di 512 bytes viene trasmesso, la MAC interface del mittente gli aggiungera un padding per raggiungere la grandezza minima


VLAN
Standard associato: IEEE 802.1Q
Il campo type/length presente nell'header di Ethernet viene sostituito da un campo type settato a 8100Hex, che indica il VLAN protocol ID
I successivi 2 byte indica altre informazioni tra cui gli ultimi 12 bit rappresentano il VLAN identifier che permette l'identificazione della VLAN del mittente
I successivi 2 byte sono invece per il campo length che conterra la lunghezza del payload (campo type/length di Ethernet)

In ogni tabella di routing viene quindi aggiunto una colonna per le VLAN
I frame nelle VLAN non vengono solo instradate secondo il loro MAC address ma anche secondo il proprio VLAN identifier in quanto end system di due VLAN diverse non possono comunicare



Le differenze nelle varie LAN avvengono solo a livello fisico
Il logical link control sublayer viene quindi diviso in
- Physical layer
Grazie alla media-independent interface MMI permette l utilizzo di diversi tipi di media e diversi bit rate in modo trasparente al MAC layer
Quando il bit rate supera i 10Mbps non è piu possibile utilizzare la codifica di Manchester
- MAC sublayer
Definisce delle primitive 
- LLC sublayer
Il protocollo LLC si base su HDLC 
Supporta sia la modalita best-effort connectionless sia quella affidabile connection-oriented
Il network layer utilizzera i servizi concessi dal MAC sublayer


CAP 6
Il routing e il forwarding vengono associate al livello di network
in TCP/IP viene utilizzato il protocollo Internet (IP), che da un servizio best-efford

Il protocollo IP in ogni host ha un indirizzo unico all interno di Internet
Ogni indirizzo IP ha due parti 
- NetID 
- HostID

L'allocazione dei NetID è gestita dal ICANN

La tabella di instradamento permette di ruotare ogni pacchetto ad ogni altro network in Internet
Alla ricezione del pacchetto, il router legge semplicemente il NetID dall header e lo usa nella tabella di instradamento per mandare il pacchetto al destinatario

SE la dimensione del pacchetto è maggiore della dimensione massima del frame (MTU Maximum Transmission Unit), lo divide in piu blocchi con la frammentazione.

Protocolli
- ARP Address Resolution Protocol: usato da IP negli host attaccati ad una LAN per determinare il MAC address dato un IP
- OSPF Open Shortest Path First: è un protocollo di routing 
- ICMP








