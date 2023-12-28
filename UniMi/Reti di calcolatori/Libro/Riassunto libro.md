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
- ICMP: usato da IP in un host/gateway per scambiarsi messaggi con un altro IP in un altro host/gateway


IP
Composizione pacchetto IP
- Campo version: specifica se sia un IPv4 o IPv6
- Campo IHL Intermediate Header Length specifica la lunghezza dell'header come multiplo di 32 bit. La lunghezza minima senza opzioni è di 5, mentre il massimo permesso è 15.
- Campo TOS Type Of Service specifica la priorita dell'applicativo e gli attributi relativi al path da seguire
- Campo Total length (16 bit): definisce la lunghezza totale del pacchetto (header+payload). La lunghezza massima del pacchetto è di 64k-1 bytes. Questo campo sarà utilizzato dalla destinazione per riassemblare il payload
- Campo Flag bits (3 bit): 
	- -
	- D bit indica se il pacchetto è stato frammentato o meno
	- M bit More fragment indica SE se ci sono altri frammenti del pacchetto (sara 0 sull ultimo frammento)
- Campo Fragment Offset: indica l'offset, in multipli di 8 bytes, rispetto all inizio del pacchetto
- Campo Time To Leave: definisce il tempo massimo per il pacchetto in transito, verra decrementato in ogni gateway/router. E' usato per rilevare eventuali loop
- Campo Protocol: usato per permettere alla destinazione IP di passare il all'interno di ogni pacchetto ricevuto allo stesso protocollo che ha mandato i dati (es ICMP or TCP or UDP)
- Campo Header checksum: per rilevare errori
- Campo Source IP address e Destination IP address (entrambi su 32 bit)
- Campo Options: puo contenere per esempio il path da seguire per raggiungere la destinazione 


Frammentazione
SE la dimensione del pacchetto è superiore al MTU del network di destinazione, è necessario dividere il payload in un numero di pacchetto con dimensione ridotta, i frammenti
Sara l'IP destinazione a riassemblare i pacchetti.

Il valore del campo Identification è uguale in tutti i frammenti, in modo che l'IP destinazione li associ allo stesso pacchetto originario 
Il campo Total length è il numero di bytes del pacchetto originario (inclusi i 20byte di header)
Il campo Fragment offset indica la posizione dei dati in ogni frammento rispetto all'inizio del payload (in multipli di 8 bytes)
Il campo M-bit è 1 in ogni frammento e 0 nell'ultimo


IP address
Dato l'aumento degli utilizzatori di Internet, si è dovuto pensare a modi piu efficienti di gestire i 32bit degli indirizzi
- Class-based addresses: vengono definite delle classi per gli indirizzi con una diversa divisione tra NetID e HostID
- Subnetting
- Classless addresses: la parte della rete di un indirizzo IP puo essere rappresentata da un qualsiasi numero di bit, portando ad utilizzo piu efficiente dello spazio di indirizzamento
- NAT Network address translation: alloca un singolo indirizzo IP ad ogni rete di accesso utilizzato da tutti gli host di quella rete
- IPv6


Class-based addresses
I 32 bit degli indirizzi vengono divisi in 5 formati, ognuno con intento di utilizzo in base alla dimensione della rete
- Classe A 7 bit per NetID e 24 per l'HostID
- Classe B 14 bit per il NetID e 16 per l'HostID
- Classe C 21 bit per il NetID e 8 per l'HostID

Casi particolare
- NetID di soli 0: indica la stessa rete del mittente
- Indirizzo a tutti 1: broadcast nella stessa rete del mittente
- HostID di soli 1: broadcast sulla rete destinazione
- Un indirizzo di classe A di soli 1 è utilizzato per il test, loopback address


Subnetting
Disaccoppiare i router associati ad una rete con le funzioni di routing della rete globale
Ogni LAN è considerata una subnet ed è indentificata dall'HostID. Quest'ultimo sara diviso in una parte di subnetid e da una che identifica  l'HostID locale
Il NetID è considerato per il routing all'interno di Internet

Per identificare i limiti del subaddress viene utilizzata una maschera dell'indirizzo


Classless addresses
CIDR Classless Inter domain routing
Vantaggi: uso piu efficiente dello spazio di indirizzamento
Svantaggio: complicazione del routing dei pacchetti

Il punto di divisione tra NetID e HostID è definito da una maschera dell'indirizzo
Ogni router della rete contiene una copia della maschera in modo che un router, leggendo l'IP destinazione, lo metta in AND e controlli se c è una corrispondenza con gli indirizzi salvati nella RT


NAT Network Address Translation
Per ogni rete di accesso, viene assegnato un solo indirizzo IP
All'interno dell'header TCP vi è il numero della porta dell'origine che identifica l'applicazione che ha fatto la richiesta e il numero di porta della destinazione che identifica la corrispondente applicazione del computer remote
Associato al router NAT, vi è una NAT table in modo che contenga per ogni sessione due entry.
- Lato richiedente, l'entry comprende l'IP privato dell'interfaccia dell'host e il numero di porta d'origine allocato
- Lato ISP, l'entry è composta dall'IP e da un numero di porta assegnato dal NAT router
In questo modo si evita che si utilizza la stessa porta TCP in diversi host


Routing algorithms
Rappresentazione del grafo della rete: ogni linea è rappresentata da due numero (IDLinea, costoAssociato)
Il costo associato a una linea è usato duranti il routing come metrica del routing/path cost (es numero di hop)

DV Distance Vector routing
L'algoritmo distribuito di instradamento DV permette ad ogni router di costruire una tabella di instradamento (il vettore) che contiene il costo del cammino (la distanza) per ogni NetID raggiungibile

1. Inizialmente ogni router conosce solo i NetID connessi direttamente ed i relativi costi: queste informazioni vengono salvate in una tabella delle adiacenze
2. Ad un intervallo di tempo prefissato, ogni router manda una copia del proprio DV ad ogni vicino.
3. In base alle informazioni ricevute, ogni router procede ad aggiornare la propria tabella di instradamento in base al DV

RIP Routing Information Protocol usa l'algoritmo DV 


LS Link State
L'algoritmo LS è usato per permettere ad ogni router di determinare la topologia della rete ed i costi associati ad ogni link in modo che ogni router possa eseguire autonomamente l'algoritmo di Shortest-Path-First (Dijkstra)

1. Inizialmente ogni router conosce solo le informazioni dei linkk adiacenti
2. Ad intervalli regolari, ogni router fa broadcast del proprio LS (quindi lo invia a TUTTI), che contiene l'ID del router e le informazioni associate
3. Dato che ogni router ha eseguito la stessa procedura, ognuno avra derivato la propria topologia e avra determinato ogni NetID connesso ad ogni router
4. A questo punto ogni router puo eseguire l'algoritmo di Shortest-Path-First per determinare il cammino minimo da se stesso a tutti gli altri router

Per evitare che uno stesso LS sia ripetuto, alla creazione viene assegnato un sequence number 
Viene inoltre aggiunto un valore di timeout che viene decrementato da ogni router in modo da poter scartare il LS se è a 0


Tunneling
Il Tunneling viene utilizzato quando IP deve comunicare con una rete con un protocollo diverso da IP.
Viene quindi introdotto un device, un router multiprotocollo, connesso ad ogni LAN.
Questo router utilizza due protocol stack, l'IP e l'altro protocollo della rete.
La rete IP quindi manda il pacchetto al router multiprotocollo che riconosce che il NetID nella destinazione è per la rete non IP. Procede a incapsulare il pacchetto nel protocollo utilizzato dalla rete destinataria in modo che la presenza di questo ulteriore protocollo sia trasparente ad entrambi gli host


Broadcast routing
- Broadcast limitato: manda una copia del pacchetto in ogni host della stessa LAN, per far cio l'IP destinazione è settato a 255.255.255.255
- Broadcast nella subnet: usato per mandare una copia del pacchetto in ogni host attaccato alla subnet specificata, per far ciò l'HostID deve essere di tutti 1


Spanning tree broadcast
Consideriamo una rete che usa LS e che è composta da diverse subnet
Con l'algoritmo di spanning tree, ogni router deriva una spanning tree dalla topologia corrente per evitare il loop di frame nella rete globale

Vengono definite le porte associate ad ogni subnet come Root Ports RP o Designated Ports DS
Tutte le porte RP/DS vengono settato in uno stato di forwarding mentre le altre in uno stato di non forwarding

Il numero di porta associato ad ogni subnet è determinato dall'identificato della subnet
Ogni SR ha una Root Port associata che è la porta con il cammino minimo per il root
Per ogni subnet, c è una DP che è la porta con il cammino minimo dalla root
Solo una copia del pacchetto viene mandato in broadcast nella rete


Routing in Internet
La struttura di Internet è una rete di reti, in particolare sono definiti diversi Tier
- Tier 3: reti di accesso
- Tier 2: gateway della rete regionale
- Tier 1: backbone network

I backbone regionali sono connessi insieme da degli NAP Network Access Point
La struttura generale è di tipo gerarchico: coinvolge un numero elevato di AS Autonomous Systems che sono a loro volta interconnessi con il backbone intercontinentale
Ogni Tier 3 e Tier 2 in una AS è chiamata area
Il protocollo di ruoting all'interno degli AS è il RIP o l'OSPF
Il protocollo di routing per far comunicare gli AS (nel Tier 1) è il BGP


ARP e RARP
ARP è usato da IP negli host collegati a una LAN
ARP è infatti utilizzato per determinare l'indirizzo MAC di un host della rete LAN dato l'indirizzo IP
Ogni host ha infatti associato un indirizzo IP e un indirizzo MAC in una ARP cache

1. Alla ricezione di un pacchetto IP, l'ARP legge l'IP destinazione e determina se l'indirizzo MAC sia gia presente o meno nella sua cache 
2. SE non è presente, fara un broadcast dei una ARP request nella LAN, che contiene sia l'IP/MAC dell'host ARP che l'IP destinazione di cui si sta richiedendo l'indirizzo MAC
3. L'host di cui si sta richiedendo l'indirizzo MAC, riconoscere il proprio IP nella ARP request e mandera un ARP reply contenente il proprio indirizzo MAC
4. L'host riceve l'ARP reply e aggiunge una entry nella propria cache

L'ARP nel gateway della rete è conosciuto come proxy ARP

RARP Reverse Address Resolution Protocol è utilizzato dagli host non appena entrano in servizio in modo che inviino con un broadcast e quindi anche al server ARP il proprio MAC address.
Il server, riconoscendo che è un messaggio RARP, crea una RARP reply contenente la coppia MAC/IP

Sia ARP che RARP hanno una lunghezza fissa d i28bytes
- Campo HW Type: specifica il tipo di indirizzo MAC 
- Campo Protocol Type: indica il tipo di indirizzo di rete usato (es per IP è 0800 in HEX)
- Campo Operation:
	- ARP request: 0001
	- ARP reply: 0002
	- RARP request: 0003
	- RARP reply: 0004
- Campo Indirizzo MAC del mittente
- Campo Indirizzo IP del mittente
- Campo Indirizzo MAC della destinazione
- Campo Indirizzo IP della destinazione


DHCP
DHCP Dynamic Host Configuration Protocol permette di ottenere un indirizzo IP a nome dell'host
E' quindi un protocollo client-server che segue 4 fasi
1. DHCP discovery: mandato dal client a tutti gli host in broadcast (255.255.255.255) e l'indirizzo mittente di 0.0.0.0. Il messaggi contiene un ID della transazione cosi che il client riconosca la sua richiesta una volta che riceve una risposta dal server
2. DHCP offer: restituita dal server, contiene il ID della transazione, una proposta di un IP, la maschera per l'IP e la durata della validità dell'indirizzo.
3. DHCP request: è la riposta all'offerta e  contiene gli stessi parametri dell'offerta
4. DHCP ACK: risposta del server che contiene gli stessi parametri in modo che il client comprenda che ora il suo nuovo IP è valido

OSPF
Open Shortest Path First
Tipi di router
- Router interni: localizzati in aree NON backbone
- Router backbone: localizzati nei backbone degli AS
- Router di frontiera dell'area
- Router di frontiera: collegato il backbone dell'AS all'Internet Backbone

Ogni router usa l'algoritmo del cammino minimo.
OSPF permette di eguagliare il traffico su due path con lo stesso costo
Una volta che l'albero SPF è stato creato, ogni router crea la propria tabella di routing
Un router è assegnato come designated router per l'AS backbone e tutti i router adiacenti.
Lo scambio di informazioni per il routing avviene SOLO tra i ruoter e il designated router


BGP
BGP NON comunica i costi ai suoi router adiacenti MA condivide il path da seguire
In questo caso il costo viene determinato anche in base a problemi politici


ICMP
Dato che IP è un servizio best-efford, i pacchetti potrebbero essere scartati mentre sono in transito.
SE un pacchetto è scartato per qualsiasi motivo tranne la corruzione di informazioni, ICMP Internet Control Message Protocol nell'host che scarta il pacchetto, genera un messaggio di errore che viene mandato al mittente, in particolare all'ICMP del mittente

SE un'amministratore di rete riceve come messaggio che una destinazione non risponde, la causa puo essere determinata utilizzando la funzione di reachability testing implementata con il ping. Viene inviata una echo request che una volta ricevuta dall'ICMP, ritorna una echo reply


QoS Support
Una congestione avviene quando la domanda per una risorsa della rete eccede il livello che concede.
SE un burst di pacchetti arriva al router su un numero differenziato di linee di input, l'output si congestionerà SE il rate d'arrivo è maggiore di quello di uscita

Ogni linea di output ha una politica FIFO
Ogni pacchetto ha una serie di parametri che definiscono i suoi requisiti di QoS

Integrated services
Inizialmente i servizi erano text-based, insensibili a delay e jitter (es FTP e email)
Ora con servizi come speech e video, i pacchetti richiedono di viaggiare in real time
Per definire che tipo di servizio viene richiesto, vengono modirficati i bit del campo Type of service

Token bucket filter
Utilizzato per garantire i requisiti di banda, delay e jitter
Ad ogni flusso viene associato un contenitore, bucket, di token che vengono immessi ad un rate determinato dalla larghezza di banda richiesta
La dimensione del bucket è la stessa del massimo spazio della coda
In questo modo SE ci sono sufficienti token, il pacchetto è messo in coda e il corrispondente numero di token viene prelevato 
mentre SE non ci sono abbastanza token, il pacchetto viene scartato

WFQ Weighted Fair Queuing
Per assicurare che il limite di delay per ogni flow sia rispettato, l'ordine di trasmissione, quindi la coda, viene modificato ogni volta che un pacchetto arriva
Quando un nuovo pacchetto arriva, gli viene assegnato un time-stamp determinato dal tempo di arrivo e dal tempo di partenza previsto
Il time-stamp è utilizzato per compararlo a quello degli altri pacchetti in coda, inviando quello con time-stamp piu piccolo
In questo modo vengono rispettati i limiti sul delay

RED Random Early Detection
Usato con le code best-efford
Un router normalmente scarta i pacchetti se la coda è piena
Con TCP ogni volta che un pacchetto è perso, la sorgente lo rileva e dimezza il suo rate per nuovi pacchetti. Questo pero causa un riempimento dello code e una perdita di pacchetti 

Con RED quando un pacchetto arriva e la coda è piena, un pacchetto che è nella coda viene selezionato randomicamente e scartato. In questo modo un numero ridotto di diversi applicativi è coinvolto e viene migliorato l'utilizzo di banda
vengono definiti un minimum threshold MinTH e un maximum threshold MaxTH e viene continuamente monitorato la lunghezza media della coda AvrLEN
Casi:
- SE AvrLEN < MinTH: il nuovo pacchetto entra nella coda
- SE AvrLEN < MaxTH: il nuovo pacchetto è scartato
- SE MaxTH < AvrLEN < MinTH: un pacchetto nella coda viene randomicamente selezione, scartato e il nuovo pacchetto entra nella coda

Differentiated services
Flow singoli in ogni classe di servizio vengono aggregati
I pacchetti in arrivo vengono classificati dai router 
Il campo TOS è sostituito da un nuovo campo chiamato differetiated services DS
In una rete DiffServ, un livello di risorse definito in termini di memoria delle code viene allocato ad ogni classe di traffico usando per es il token bucket filter


MPLS
Come un pacchetto viene inviato in una rete IP standard
Alla ricezione del pacchetto da una linea di input, il router legge l'IP destinazione nell'header per determinare il NetID utilizzando la maschera
Usa il NetID per determinare la porta di uscita grazie alla tabella di instradamento
Il campo ToS nell'header viene passato al classificatore di pacchetti che determina la coda e le regole di scheduling da applicare al pacchetto. Cio determina la porta di uscita da utilizzare per mandare il pacchetto al prossimo hop.
Una regola di coda e scheduling vengono usate per ogni classe per assicurare che i requisiti di QoS vengano rispettati

MPLS MultiProtocol Label Switching è una tecnica utilizzato dai router in una backbone area
Una volta che il traffico è stato classificato e messo in coda, il AG scheduler separa i vari traffici, fa shaping

Ogni area border router ABR riceve pacchetti da una serie di access gateway e è anche un LER Label Edge Router in quanto aggiungono e rimuovono MPLS header
Difatti le label MPLS hanno significato SOLO nel singolo hop, in modo che i pacchetti siano forzati a seguire uno specifico path (LSP label switched path)
I backkbone routers nel AS leggono semplicemente la label e mandano il pacchetto alla porta di output con una nuova label, label switching

- La lunghezza dell'header MPLS è di 20bit per la label
- 3bit per CoS usato per selezionare la specifica coda 
- 8 bit di time to live per riscontrare loop

Viene utilizzato un approccio CR Constraint Routed LSP in modo che ci sia un Network Management che riempie le tabelle utilizzate per fare label switching


IPv6
Nonostante CIDR abbiamo esteso lo spazio di indirizzo di IPv4, si è introdotto l'IPv6
Feature
- Spazio di indirizzamento aumentato da 32 a 128 bits
- Header semplificato permette ai router di processare e instradare i pacchetti piu velocemente
- migliorata la sicurezza

Formato:
Header di 40 bytes
- Campo Version 4 bit: settato a 6
- Campo Traffic class 4 bit: simile a ToS. Permette al mittente IP di allocare una diversa priorita ai pacchetti
- Campo Flow label 20 bit: settato a 0 SE è un pacchetto best-efford altrimenti è usato per permettere al router di identificare i pacchetti di una stessa sessione
- Campo Payload length: indica il numero di bytes che seguo l'header di 40 bytes (ATT nell'IPv4 questo campo comprendeva anche l'header). MIN: 536 bytes, MAX 64kk bytes
- Campo Next header: IPv6 comprende un header principale seguito da altri header tra cui quello di TCP/UDP, oppure da extensions headers inserti tra quello principale e l'header del livello di trasporto
- Campo Hop limit: simile a time to leave ma stavolta vengono contati gli hop, venendo decrementato di 1 ogni volta che viene inviato
- Campo Source/Destination address 128 bit: IPv6 è assegnato all'interfaccia fisica NON all'host o router


Extension headers
Tipi previsti
- hop-by-hop options: informazioni per i ruoter visitati durante il path
- routing
- fragment: informazioni per permettere alla destinazione di riassemblare il pacchetto

Hop-by-hop options
Informazioni che devono essere esaminate da ogni router che il pacchetto visita
Next header = 0
Quando è necessario trasferire pacchetto molto superiori al MTU, i pacchetti che contengono questo header si chiamano jumbograms
Questa option contiene solo il campo jombo payload length

Routing
Next header = 43
Contiene 24 bit di stirct/loose map i quali SE il bit = 1, l'indirizzo specificato deve essere raggiunto in modo diretto, mentre SE bit = 0, l'indirizzo puo essere raggiunto passando da altri indirizzi.
Contiene poi al massimo 24 indirizzi a cui fa riferimento la mappa


IPv6/IPv4 interoperability
E' necessario permettere di lavorare tra due reti con indirizzi di livello diverso
1. Dual protocols
Sono presenti host con IPv4 e altri con IPv6. Il server ha sia un protocollo IPv4 e IPv6  in modo che riesca a leggere il campo version dei vari pacchetti e passare i pacchetti al corretto IP

2. Dual stacks and tunneling
Per interconnettere reti con rispettivamente IPv4 e IPv6, è necessario che il server, avendo sia un protocollo IPv4 che IPv6, applichi un tunneling dell'IPv6 in un IPv4

3. Translators
Alla ricezione di un pacchetto IPv6/IPv4, questo viene convertito in un pacchetto IPv4/IPv6 grazie a una NAT con un PT protocol translator
SE la NAT è utilizzata come gateway della rete, allora è una NAT-PT gateway
Per l'assegnazione degli IPv4, solitamente la NAT alloca un certo numero di hostid per le destinazioni, applicando un timeout a tali indirizzi


CAP 7
TCP Transmission Control Protocol fornisce un servizio addidabile orientato alla connessione
UDP User Datagram Protocol fornisce un servizio best-efford senza connessione

TCP deve convertire il servizio best-efford di IP in un servizio affidabile
Un nuovo numero di porta è allocato ad ogni nuova richiesta di trasferimento
In particolare si allocano le porte da 1024 a 5000
Le porte da 1 a 1023 sono tipicamente riservate (es porta 21 riservata a FTP)

TCP divide lo stream di byte in blocchi chiamati  segmenti
Le due entita TCP accordano un MSS Maximum Segment Size che di standard è di 536byte

Il protocollo TCP ha 3 operazioni distinte:
- Apertura della connessione
- Trasferimento dei segmenti
- Chiusura della connessione 

Apertura
Alla ricezione della primitiva connest() dall'applicativo, inizia la fase di apertura della connessione
1. TCP manda manda un segmento al server con flag SYN e SEQ=X con X numero di inizio sequenza. Il mittente entra nello stato di SYN_SENT
2. Alla ricezione del segmento, SE il server non è in ascolto, la connessione viene abortita mandando un segmento con il flag RST. In caso contrario il server manda un segmento con il flag SYN, la propria SEQ, il flag ACK e come ACK X+1 per segnalare di aver ricevuto il segmento X al client. Il server entra in stato di SYN_RCVD
3. Alla ricezione del segmento, il client manda un segmento con ACK, ACK = Y+1. La connessione lato client è ESTABLISHED
4. Lato server, alla ricezione dell ACK, entra in stato di ESTABLISHED

In ogni segmento TCP è inclusa la window size, cioè il massimo numero di byte che è disposto a ricevere, window size advertisement

Per ridurre il numero di segmenti inviati, TCP NON ritorna immediatamento l ACK quando riceve un segmento senza errori MA aspetta, tipicamente 200ms, per vedere se ci sono dati che vengono messi nel buffer send: delayed acknowledgments

Una variazione del delayed acknowledgement, è l'algoritmo di Nagle
TCP in questo caso aspetta solo un segmento che receve l ACK. Quando l ACK arriva, tutti i caratteri nel buffer, vengono inviati in un unico segmento

Controllo degli errori
TCP ritrasmette un segmento SOLO quando riceve 3 ACK duplicati per lo stesso segmento
Quando si rileva la perdita di un segmento, un RTO inizia per il nuovo segmento che deve essere trasmesso
Quando la ritrasmissione avviene prima dello scadere dell RTO, in quanto ho ricevuto 3 ACK duplicati, si parla di Fast Retrasmission

La scelta del dimensionamento dell RTO è un fattore critico delle performance
La scelta dell RTO deve essere dinamica
L'approccio iniziale deriva dall utilizzo dell'Exponential Backoff
Viene settato RTO inizialmente a 1,5s, e viene duplicato quando avviene una ritrasmissione per un massimo di RTO=2m

Successivamente RTO si deriva dal RTT
RTO viene aggiornata per ogni misurazione del RTT
$$RTT = \alpha * RTT + (1-\alpha ) *M$$
con M la misura dell RTT e alpha un fattore

Nella maggior parte delle implementazione, TCP restituisce un ACK per ogni segmento che riceve corretto. Quando invia un ACK, un timer, delayed ACK timer, viene avviato e un secondo segmento non dovrebbe essere ricevuto prima che scada


Controllo di flusso
Il campo window size di ogni segmento indica il numero di byte che il TCP ricevente puo ricevere nel buffer. In questo modo si garantisce che ci sia sempre spazio libero nel buffer del destinatario prima che la sorgente mandi i dati.

Associata ad ogni direzione vengono mantenute due variabili, la finestra di invio W_S, e la finestra di ricezione W_R
Il flusso si ferma quando W_S = 0 
W_R invece è aumentata quando riceve dei dati privi di errore e viene diminuita quando AP destinatario legge dei byte dal buffer

Controllo di congestione
Un segmento potrebbe essere scartato durante il suo viaggio perche sono presenti degli errori o perche un router/gateway è diventato congestionato.
Ogni RCP ha quindi una variabile chiamata finestra di congestione W_C

Inizialmente non si conosce lo stato delle rete quindi si individuano 3 fasi:
- Slow start: in cui W_C viene aumentato di 1 per ogni ACK ricevuto in modo da aumentare rapidamente. Questa fase prende il nome di slow start in quanto W_C inizialmente è uguale a 1
- Fase di prevenzione della congestione: lo slow start si ferma quando raggiunge lo Slow Start Threshold SST (tipicamente a 64kbytes). Nella nuova fase W_C viene incrementato di 1 ogni W_C ACK ricevuti 
- Fase costante in cui W_C non aumenta

Tipi di congestione:
- Ricezione di ACK duplicati: indica che la destinazione è raggiungibile quindi si presume un livello di congestione basso. Alla ricezione di 3 ACK duplicati, W_C viene dimezzato e viene utilizzato l incremento della fase di prevenzione della  congestione (fast recovery)
- RTO scade: assumendo che lo scadere dell RTO sia un evento raro, cio indica una congestione grave. W_C è quindi resettato a 1 e si riparte con lo slow start

Chiusura della connessione
- 4 way close
In tutti gli esempi di chiusura di connessione, entrambe le entita sono in uno stato di ESTABLISHED EST
- AP dell host manda una primitiva close(), cosi il suo TCP manda un segmento con FIN=1 e SEQ=X (con V(S) = X) entrando in uno stato di FIN_WAIT1
- Il TCP che riceve il segmento FIN, ritorna il segmento con ACK = 1 e ACK = X+1, entrando nella fase di CLOSE_WAIT in cui dopo aver usato la primitiva receive(EOF), sta aspettando dall AP la primitiva close()
- Nel frattempo l'altro host, alla ricezione dell ACK, entra in uno stato di FIN_WAIT2 attendendo il segmento con FIN dall altro host
- Quando l'AP dell altro host fa la close(), viene mandato un segmento con FIN=1 e SEQ= Y (con V(R) = Y) entrando in uno stato di LAST_ACK
- Alla ricezione del FIN, il TCP ritorna un ACK e fa partire un timer di 2 MSL entrando in una fase di TIMED_WAIT in cui allo scadere del timer considera la connessione chiusa (MSL Maximum Segment Lifetime)
- L'altro host, alla ricezione dell ACK, chiude la connessione

- 3 way close
La procedura è simile al 4 way MA il primo ACK viene mandato congiuntamente al secondo segmento con FIN, quindi un unico segmento con FIN=1, ACK = 1, ACK = X+N+1

- half-close
Potrebbe succedere che nonostante un AP abbia finito la trasmissione e voglia chiudere la connessione, si aspetti comunque di ricevere altri dati
- Non viene utilizzata la primitiva close(), MA shutdown(). TCP infatti con tale primitiva lascia il path EST in ricezione, mandando il segmento FIN e entrando in FIN_WAIT1.
- Alla ricezione del segmento, TCP manda una receive(EOF) alla propria AP in modo da indicare che non ricevera altre informazioni. Entra in uno stato di CLOSE_WAIT, potendo ancora inviare dati per cui ricevere un ACK
- Quando avra terminato l invio dei dati, l AP usera a sua volta la primitiva shutdown, e il TCP mandera un segmento di FIN = 1, SEQ =  Y + N.
- L'altro Host alla ricezione del segmento, mandera una primitiva con receive(EOF) e mandera un segmento con ACK=1, ACK= Y+N+1. Entra cosi in una fase di TIMED_WAIT in cui allo scadere del timer di 2MSL, chiude la connessione
- L'altro Host alla ricezione dell ACK, chiude la connessione

Additional features
- Persist Timer
Il pacchetto con il Window update potrebbe andare perso MA cosi la finestra resterebbe a 0 e ri rimarrebbe in un deadlock
Per risolvere cio quando viene settata la finestra W_S, parte il persist timer che SE prima del suo scadere non viene ricevuto un segmento con WIN = ..., allora TCP manda un window probe

- Keepalive timer
Quando una connessione è stabilita tra due entità, questa persiste finche una delle due non la chiude. MA SE il client viene spente, la connessione rimane anche se è inattivo.
Il server TCP tiene quindi un keepalive timer di 2 ore al cui scadere verra inviato un segmento di cui si aspetta un ACK. SE non lo si riceve, si riprova per 10 ogni ogni 75s e nel caso si termina la connessione

- Silly window syndrome
In alcune AP si potrebbe richiedere di leggere o inviare un basso numero di byte, intansando la rete con moltissimi segmenti
Per evitare cio, un TCP ricevente non invia la window update finche non c è sufficiente spazio nel buffer 

- Window scale option
Il campo window size nell header è di 16 bit, permettendo una dimensione massima di 2^16.
Tuttavia per avere una dimensione maggiore, si utilizza la window scale option (inclusa nel segmento SYN)
Formato:
- NOP option: 8 bit con valore 1 usato come padding
- Kind = 3
- length = 3
- Shift count: il window size è ottenuto moltiplicando per 2^n con n il valore nello shift count. es shift count = 14 (il suo max), $65 535 * 2^{14}$

- Time stamp option
Utilizzato per ottenere una stima piu accurata del RTT
Ad ogni invio di dati, il TCP legge il current time e scrive nel campo time stamp value e quando il TCP restituisce un ACK, scrive il time stamp nel time stamp echo reply

- SACK permitted option
Simile al selective repeat nel L2 ma il segmento contiene una lista dei segmenti mancanti in modo che tutti i segmenti siano trasmessi in un unico RTT


UDP
Ogni messaggio UDP è trasmesso direttamente al singolo IP datagram infatti viene demandato al layer IP su Internet
NON ci sono controllo dell'errore, di flusso e non c è una fase di setup della connessione 

Formato
- source/destination port su 16 bit: numero di porta del protocollo applicazione 
- length: numero di byte header (8 byte) + dati
- checksum
- dati


CAP 8
DNS Domain Name System
Permette ad ogni host in Internet di allocare un nome simbolico ad un indirizzo IP
Viene utilizzata una struttura gerarchica in cui al livello piu alto c è la root domain seguita dai codici dei paesi o generic domain, seguiti dal codice dell area e cosi via.
L'assegnamento del codice dei paesi avviene a livello internazionale.
La struttura gerarchica permette di partizionare il DNS in maniera locale

Formato
Il domain name è il nome del dominio a cui il record si riferisce
Il FQDN Fully Qualified Domain Name deve essere meno di 256 caratteri con l ultimo byte a 0 (la root)
Il campo type indica il tipo di record es type-A = IPv4, type-AAAA = IPv6, type-MX = nome dell host che attende la mail
Il campo class è sempre a 1 perche indica l utilizzo di Internet
Time to live indica i secondi di validita del IP che si riceve (es 2 giorni = 172 800)

Per instanziare una query ad un DNS, si aggiunge l header di 12 byte  alla quey ottenendo un DNS query message. Il DNS response message invece si otterra accodando alla query una serie di record

Ogni zona ha associato un server primario e una secondario per il DNS

Ogni root server tiene il nome e l'IP di ogni server di secondo livello della gerarchia e cosi via

Un AP ottiene un indirizzo IP da un nome dell host attraverso un SW chiamato resolver
Il risolver, a cui è dato l indirizzo IP del server primario e secondario del DNS, puo richiedere l'IP del domain name, sapendo la porta nota sui server (53)

Risoluzione ricorsiva
Quando un local name server non contiene l IP per il domain name richiesto, richiede ricorsivamente tale informazione facendo a sua volta una DNS query in modo gerarchico (root -> country -> ...)


Email
Un email client è un SW chiamato UA User Agent. Fornisce un interfaccia utente per creare, inviare e ricevere mail 

UA mantiene una mailbox in IN e OUT. Il SW associato alla funzione di invio è chiamato MTA Message Transfer Agent
Il protocollo POP3 è utilizzato per fare il fetch dei messaggio in IN
Il protocollo SMTP Simple Mail Transfer Protocol è invece utilizzato per l'invio 

L'indirizzo mail è considerato come un domain name formato da due parti  separate dalla @

Il messaggio è composta da un header e da un body
Ogni campo nell'header comprende una singola linea di un testo ASCII con il nome del campo (standardizzato) mentre una singola linea è usata per separare l header dal body
Per rappresentare la EOL si utilizza un CR Carriage return e un LF Line Feed
Per permettere l'invio di diversi materiali multimediali, si utilizza il protocollo MIME Multipurpose Internet Mail Extension

Content-Description: descrizione testuale
Content-Id
Content-Type: definisce il tipo di informazioni nel body

Il base64 è usato per mandare blocchi di dati in binario, aumentando pero la dimensione del messaggio

Trasferimento del messaggio
- Quando un utente preme sul tasto SEND, lo UA formatta il messaggio e lo invia allo UA del server nel suo server di mail locale
- Alla ricezione, deposita il messaggio nella coda del MTA che controlla a intervalli regolari la sua coda. Una volta relevato il messaggio legge il campo From e To e li scrive in MAIL FROM e RCPT TO.
- Prima di mandare il messaggio, l MTA deve risolvere l indirizzo mail del destinatario grazie al DNS
- Una volta ottenuto l IP, ogni messaggio è trasferito con una connessione TCP sulla porta 25 (SMTP)

CAP 9 
HTTP è il protocollo standard a livello applicazione.
E' usato per ottenere informazioni 
La porta di HTTP è la 80
Quando un browser ha una richiesta HTTP, inizializza una connessione HTTP alla porta 80 del server con domain name nell URL