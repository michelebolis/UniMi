Libri:
- Networking e Internet Pearson 5a edizione
- secondo libro solo ultima parte del corso
NO LUCIDI

Esame:
- Teoria: risposta libera a 10 domande di ragionamento in 1ora e mezza (60%)
- Lab: 2 parti (40%)


Come Far parlare la macchina A con la macchina B?
Nei Server all'inizio risiedevano solo i contenuti: la macchina A poteva depositare contenuti o richiederli. 

La rete permette di far comunicare le macchina con le macchine server
Oggi i contenuti delle macchine server sono cambiati, infatti non sono solo di archiviazione ma è anche sistema che eroga servizi per l'utente

I sistemi-cloud sono sistemi di rete connessi ad altissima velocita per erogare servizi all'utente attraverso il plugin installato sulla macchina dell'utente
I sistemi cloud pero ora sono usati per quei servizi che non hanno problemi di tempo, infatti per ogni richiesta è necessario un Δt, che è variabile (es contenuto richiesto contemporaneamente da molti utenti).

Se tempo è troppo variabile diventa un problema

Il cloud si sposta sempre piu vicino all'utente. Si copia il contenuto in vari punti strategici attraverso un servizio di CDL Content Delivery L, e successivamente sarà necessario un updating.

Requisiti della rete:
- Affidabilità: se A manda un contenuto a S o viceversa, quel trasferimento è privo di errori. 
	Ci possono essere diversi livelli di tolleranza dell'errore 
- Sicurezza: ma non è un problema di chi progetta la rete, è di chi progetta l'applicazione
- Prestazioni: misurabili 
	- nella **velocità di trasferimento** in funzione del bit rate dei canali
	- ... verificare se la mia rete riesce ad erogare all'utente finale la velocita promessa
- Indirizzamento: la rete deve poter indirizzare il contenuto al destinatario connesso. 
	==Ogni destinatario o mittente deve essere indirizzabile==. 
- Qualità di servizio QoS: deve riuscire ad erogare i servizi date le specifiche dell'applicazione (es tempo massimo, tolleranza degli errori...) 

Livelli della rete
1. Rete-di-accesso: qualsiasi sistema di rete (es LAN) che collega le macchine e consente di aggregare tutto il traffico da e verso la rete. Tipi di aggregatori di traffico
		1. Rete locali fissi
		2. Rete locali wireless
		3. Rete cellulare: è mobile fino a che manda il traffico ad una rete locale wireless (antenna)
2. Rete-fissa: è la rete Internet ma puo essere anche presente all'interno delle rete di accesso

Non posso tirare un filo per ogni dispositivo
Dobbiamo utilizzare dei concentratori
Per collegare i concentratori delle due reti, dati i loro indirizzi R1 e R2, non posso usare direttamente un cavo ma userò altri concentratori

La rete è quindi un insieme interconnesso di concentratori di traffico, router, che consentono di raggiungere una destinazione con un cammino multi hop (multi salto).

Router: consentono di trovare il percorso migliore per raggiungere una destinazione in quel momento.

Requisiti della rete:
- Indirizzamento
- Instradamento: sarà necessario un algoritmo di instradamento
- Affidabilità: (o forse non conviene alla rete, verra demandata al TCP, affidabile se END to END)
- QoS


Un router ha delle linee di ingresso e delle linee d'uscita, entrambi bidirezionali (porte I/O). 
I router ha un piccolo SW di instradamento che processerà le code di ingresso e uscita legate alle porte. 

I problemi sono il numero di porte e la velocita in cui operano i link di uscita e ingresso.
Il router decide in che porta mandare il contenuto in coda di uscita in base ad una tabella in cui si specifica istante per istante, il percorso migliore per ogni indirizzo raggiungibile.
SE una delle code/buffer è pieno, butto via il contenuto. Uno dei problemi dei router è la gestione della memoria. 

Si decise quindi di ==frammentare il contenuto in dimensioni massime fisse== creando pacchetti in modo da avere una gestione del traffico semplificata. 
Questa frammentazione deve avvenire lato del mittente, aggiungendo un header o intestazione con delle informazioni necessarie per il funzionamento della rete, quali l indirizzo. 

Man mano che il pacchetto viene processato dai router  aumenta di dimensione, diminuendo quando arriva al destinatario (fragmentation-assembly-deassembly)


Rete a commutazione di pacchetti:

---

ogni router ha porte I/O, ognuna con una coda (FIFO) di entrata e una coda in uscita
Periodicamente secondo un algoritmo di instradamento, facendo una codifica dei pacchetti (in particolare lo header che sicuramente contiene sorgente e destinazione), decide in che porta mandare il pacchetto.
Tabella di instradamento contiene il destinatario pacchetto e la porta di uscita

Le code hanno una dimensione finita
La sequenza prelevamento-decodifica-forward deve essere effettuata il piu velocemente possibile. Difatti l'header è nei primi bit cosi il router è piu veloce nella lettura
Piu piccoli sono i pacchetti, meno spazio occuperemo nelle code ma avremo un overhead a causa dell'header di ogni pacchetto. Serve un compromesso tra lo spazio occupato nelle code e l overhead

Tempi statici conseguenti dai tempi fisici
I tempi variabili della rete sono i tempi delle code, in quanto non so quanto sono piene e quindi quando l algoritmo decodificherà il pacchetto
In questo caso le code sono di tipo store and forward. 
Il tempo indefinito è quello che intercorre tra forward e store: Jitter.
Quanti piu nodi di reti devo attraversare, tanto piu Jitter aggiungo e quindi tanto piu la media per i pacchetti aumentera.

Sara quindi necessario una stima adattiva 

Trasmissione in banda base: quando trasmetto da 0 a Hz massimo 
ogni canale fisico ha un certo data-rate, rate di immissione 
es 1 Mbps
attaccata alla porta di rete abbiamo il bus di comunicazione con la coda di uscita $T_x$, con delle word di una certa dimensione.
Viene quindi fatta una prima conversione mandando in alternanza veloce i singoli bit (da LSB a MSB), grazie a un clock. 
es di protocollo: Lato ricevitore si rappresenta l'1 con un livello alto di voltaggio e 0 un voltaggio basso. 
Problemi: 
- Essendo pero due sistemi distribuiti, hanno due clock diversi: è necessario capire quando inizia e quando finisce un bit, saranno quindi necessari algoritmi di sincronizzazione

Tipicamente la rete non è affidabile a causa del rumore. 
Un bit potrebbe cambiare nel suo opposto
Ci sono bit aggiuntivi per
- riconoscere se c e stato almeno un bit sbagliato
- O eventualmente rimediare all'errore

La rete deve quindi essere in grado di riconoscere se un pacchetto è corretto/non alterato e rimediare all errore
Nel caso in cui il pacchetto sia arrivato corretto, ma la consegna dei singoli pacchetti non è in ordine, è necessario un meccanismo per ricomporli. In particolare oltre a sorgente e destinazione, si puo avere una serie di bit per riconoscere la posizione del pacchetto nella sequenza e la lunghezza totale della sequenza.
Potrò quindi anche riconoscere se ho ricevuto dei duplicati

Il ricevente manda al mittente un Acknoledgement (ACK) ogni volta che riceve un pacchetto corretto.
HA passa entra in uno stato di Wait una volta che ha mandato i bit da $T_x$; durante questo tempo il canale non è utilizzato.
Il problema è che l'ACK potrebbe non arrivare, in quanto potrebbe essere perso o corrotto


Il Jitter è definito dalla deviazione standard, importante per alcuni applicativi che necessitano stabilità di comunicazione (es videogiochi)
La media è comunque importante 

In realta per la maggior parte dei casi non è richiesta affidabilita ma piuttosto la velocita (es voce in videochiamata, caso contrario una mail)


La rete fornisce gli strumenti per essere configurata dalle varie applicazioni, quindi deve essere abbastanza flessibile da potersi adattare alle richieste degli applicativi.

Un protocollo è un insieme di regole e convenzioni che permettono la comunicazione due entità. Ovviamente le due entità devono usare lo stesso protocollo.


Consideriamo A e B collegati da un solo cavo
- Tempo di trasmissione $T_x = {datiDaTrasmettere \over capacitaCanale}$  
	- dipende dalla capacita del canale e dalla velocità di immissione del mittente.
- Tempo di propagazione $T_p = {distanza \over velocita}$ 
	- è il tempo che un pacchetto impiega da A a B
	- dipende unicamente dalle caratteristiche fisiche del canale su cui viaggiano i dati (lunghezza e materiale fisico)
- $T_p+T_x$ tempo che intercorre da quando il primo bit esce a quando l ultimo bit arriva
	- $T_p$ aumenta molto fino a superare Tx quando le distanze aumentano (comunicazioni satellitari, continentali)

Anche l'ACK è un pacchetto, che viaggia nella direzione opposta quindi dobbiamo considerare anche $T_xACK$ e il $T_pACK$
OSS $T_p$ e $T_pACK$ sono uguali, perche è lo stesso canale e la stessa distanza 
$T_xACK$ vogliamo che si minimizzi: per far ciò minimizziamo il peso dell'ACK, tanto da risultare spesso irrilevante nella stima del tempo.

Per riconoscere che non sia arrivato un ACK, faccio trascorrere un tempo minimo calcolato come: $T_x + 2*T_p$

Una volta inviato un pacchetto, ne tengo una copia nel buffer del Kernel finchè non mi ricevo ACK. Stessa cosa anche il ricevente, tiene una copia del pacchetto nel buffer del Kernel finchè non riceve tutti i pacchetti del file.
Una volta inviato un pacchetto, parte un timer per il Waiting che stima il tempo minimo, cioè $T_x + 2*T_p$ sovrastimato

SE ACK non arriva A non sa se è arrivato il pacchetto, quindi lo manda nuovamente. 
L'Host ricevente riconosce se il pacchetto fosse gia arrivato nei buff. Nel caso ce l'abbia già lo scarta, mandando lo stesso l'ACK al mittente.


SE la rete è affidabile e succedono degli errori, siamo in grado di risolverli dagli host (non dalla rete)

---

In $T_p$ consideriamo il tempo del singolo bit perche la capienza del messaggio totale è utilizzata nel calcolo di $T_xP_1$

In un caso piu generale oltre al tempo di propagazione del canale in se abbiamo piu router coinvolti, ognuna con le proprie code che causano un tempo di coda $T_q$.
Il tempo complessivo è piu complicato da stimare

Tempo di invio completo: $T_x+ T_p + T_q + T_xR_1 +$ ...
$T_q$: tempo di coda nel singolo router


Obiettivi per la progettazione
- Affidabilità
L'affidabilità, oltre ai messaggi, riguarda anche l'identificazione del malfunzionamento di un link.

Tipi di allocazione
- allocazione a commutazione di circuito: è richiesta una comunicazione completa, senza interruzione del traffico (es voce)
- allocazione a commutazione di pacchetto: come condividere i canali a disposizione dei vari host
	Usiamo tecniche di multiplexing per condividere i canali da piu host 
	- time division multiplexing TDM: usata nell'ambito delle reti fisse, in particolare per l upload. MA non tiene conto della priorità

Controllo per garantire l'affidabilità della rete
- Controllo di flusso: 
Il protocollo tra A e B deve essere in grado di comunicare a A di aspettare perche B sta processando (o perche ha il buffer pieno) o di far negoziare tra A e B il tempo massimo di elaborazione in base all host piu lento
es dopo poche interazione HB arriva ad avere il buffer pieno ed inizia a buttare via ciò che gli arriva 
- Controllo di congestione: 
La rete deve essere in grado di comunicare quando è congestionata. 
Una congestione avviene quando si ha una saturazione delle code dei router o ci sono dei link che causano colli di bottiglia (che si notano con l aumento dei pacchetti inviati). 
Tipi di algoritmi per la congestione:
- cercano di evitarla a priori
- aspettano finche non avviene una congestione, cercando di rimediare abbassando la velocita di trasmissione
Solitamente la perdita di pacchetti è causata da una congestione


- QoS
Oltre all'affidabilita la rete deve essere il piu possibile general purpose per offrire diverse qualità di servizi in base all applicazione utente

Le richieste/parametri di qualità di servizi sono il Jitter, il data rate, il massimo degli utenti...
SE non c è la possibilita di raggiungere le richieste, si attua una negoziazione

Difficolta: le applicazioni che utilizzano la rete sono moltissime e molto variegate
E' necessario che il router applichi una politica per la gestione delle code, per far ciò nel pacchetto i parametri di QoS sono presenti nell'header o sono presenti dei bit per identificare la classe di QoS a cui appartiene il pacchetto


- Sicurezza
Sia sul canale 
https richiede di cifrare il contenuto dei pacchetti, cifra solo il contenuto/payload


Come l hanno realizzata
Principi di ingegneria del SW
- Information hiding: incapsulare le informazioni rendendole disponibili solo attraverso delle interfacce. Nascondere anche il funzionamento del sistema ai livelli superiori

- Stratificazione della rete (semplice)
Mappatura 1:1 tra i 2 host che devono usare gli stessi protocolli
A livello piu alto abbiamo i nostri utenti
Mittente:
- La richiesta viene incapsulata nel livello 5. Utilizza un protocollo di livello 5 (i due livelli sono peer) per aggiungere alla richiesta un header di livello 5. Passa al livello sottostante il messaggio
- Il livello 4 espone delle interfacce/primitive al livello 5 (o un servizio affidabile o un servizio veloce ma non affidabile) che sceglie. Nell'header aggiunge quale servizio ha scelto il livello 5 
- Il livello 3 è in grado di fare l'instradamento, capire se c è un percorso di consegnare il messaggio 
- Il livello 2 offro anch esso un servizio affidabile e uno non affidabile, che sceglie il livello 3
- Il livello 1 richiede a che velocita vuole il trasferimento e aggiunge anche informazioni in coda
Ricevente:
- Accordo tra i 2 livello 1 è la forma d onda per capire quando il bit è 1 o 0. Il livello 1 utilizza l head del livello 1, che contiene informazioni di interesse per quel livello (es interpretazione codifica). Passa quindi al livello superiore il resto del messaggio
- Livello 2 controlla la correttezza
- Livello 3 controlla se l indirizzo è corretto
- Livello 4 controlla il servizio richiesto e se è stato rispettato 
- Livello 5 la richiesta viene processata e passata all applicativo del destinatario. Qui si torna ad avere il pacchetto originario

NIC Network Interface Card
Mittente dal livello 5 a 1 aggiunge gli header ai payload, mentre lato destinatario dal livello 1 a 5 viene usato e tolto gli header


Due modalita di utilizzo di protocollo
- Servizi orientati alla connessione: fare una connessione significare istaurare un canale (setup), il dialogo e infine una fase di rilascio. 
- Servizi senza connessione: appena ho il dato lo mando, senza contrattare i QoS

Standard teorico: ISO-OSI
- Applicazione: protocollo che mette in comunicazione due applicazioni (es http, DNS, IMAP, REST)
- Presentazione: fare in modo che i dati siano presentati opportunamente, quindi i dati sono compressi e decompressi
- Sessione: mantenimento di una connessione virtuale tra i due host
- Trasporto: 
- Rete: (es IP, Internet Protocol)si occupa di fare instradamento data una sorgente e una destinazione in multi hop (passando per piu nodi)
- Data link: (es Ethernet) si occupa di trasferire un pacchetto da una porta di un apparato dall'altro lato del cavo
- Fisico:

Fino al livello 4 tra i protocolli, i peer comunicano direttamente 
(nella foto a destra in parte sono le "unita di misura" di cio che sto trasferendo)


TCP-IP Transition Control Protocol
E' uno standard de facto
Chiamiamo i pacchetti segmenti
- Applicativo (HTTP, SMTP, DNS)
- Trasporto (TCP, UDP)
- Internet: (IP, ICMP)
- Data link: dipende fortemente dal livello fisico (DSL, SONET, 802-11, Ethernet)

Trasporto e Internet implementato nel SO
Ente di standardizzazione IEEE 802.
802.3 LAN
802.11 WiFi
802.15 Bluethoot
SE cambiano i protocolli, NON devono cambiare le interfacce tra i livelli

Tipo di comunicazione
- Unicast: unico sorgente che invia e una sola destinazione 
	- Simplex: una sola direzione, ci interessa solo mandare i dati
	- Half-duplex: canale bidirezionale ma puo essere utilizzato una sola direzione alla volta
	- Full-dupllex: comunicazione bidirezionale nello stesso istante di tempo
- Multicast: unico sorgente che invia a un sottoinsieme di host
- Broadcast: unico sorgente che invia a tutte le destinazioni


Livello fisico
Vogliamo trasmettere dei bit sul canale.
Facciamo variare un livello di voltaggio, -V per lo 0 e +V per l 1
Modulatore: modula un onda sinusoidale per darle una forma approssimata, a banda limitata cioe un certo numero di armoniche (ognuna una frequenza in Hz). 
Se uso poca banda (poche armoniche), la forma del segnale non approssima bene. 
Diminuendo banda perdo quindi la definizione del mio sistema 

In una comunicazione vi è sempre un rumore elettromagnetico che disturba la comunicazione, ma il ricevitore non puo riconoscere quale punto sia dato dal segnale iniziale e quale dal rumore. Alcuni bit potrebbero invertirsi

Cavi fisici
- Doppino telefonico (Twisted Pair): 
E' formato da coppie di cavi arrotolati tra di loro a spirale 
Le caratteristiche del cavo sono date dalla sua categoria, CAT

Per una comunicazione elettrica servono due cavi per chiudere il circuito. 
Vengono arrotolati perche quando passa la corrente induce un campo magnetico in entrambi i cavi che permette di annullarli.
Le coppie si mettono ulteriormente a coppie perche l'informazione viene trasmessa anche invertita in modo che, qualora l'informazione subisse del rumore, si annullerebbe in quanto lato destinatario di farà T1-T2 
es rumore di 3V, ciò ha influenza su entrambi quindi +3V-3V si puo eliminare

Categorie: 
- UTP Unshielded
- STP Shielded, schematura sta in un foglio di alluminio attorno ai cavi


- Cavo coassiale/coaxial: cavo di rame

- Cavo fibra ottica
E' formato da una parte di vetro in cui passa la luce
- Multimodale: la luce viaggia grazie alla riflessione continua della luce grazie ad un angolo critico per effetto della rifrazione
Lato mittente, c è un laser o un diodo che manda gli 1 o 0 mentre lato destinatario vi è un ricevitore ottico per leggere le informazioni


Differenze
- costo
- proprieta di attenuazione: la fibra ha attenuazione minore (attenuazione: diminuzione progressiva dell'intensità di un segnale) del doppino telefonico (doppino massimo teorico 100m)

---

Reti punto punto : topologia magliata in cui i nodi sono collegati 
Per affidabilità devo aggiungere delle funzioni in ogni nodo, a livello 2
OSS abbiamo un unico processo di livello 3 MA tanti processi di livello 2 quante sono le porte I/O

Per rendere un canale affidabile da un nodo A a un nodo B, voglio un riscontro del ricevente con un ACK. Per far ciò mi serve pero un timer e un buffer (lato trasmissione) e un altro buffer (lato ricevitore)
Lato trasmissione serve perche tengo il frame finche non ricevo ACK

Dimensionamento del timer
- sottodimensionamento: mi porta a ritrasmettere pacchetti in realtà già ricevuti dal destinatario
- sovradimensionamento: perdo troppo tempo ad aspettare nel caso di ACK perso o di frame non arrivato
T dovrà essere maggiore di $T_x + 2* T_p$
Timer inizializzato quando viene mandato F e resettato all'arrivo dell'ACK

per tutto il tempo $T_x$ il driver sicuramente è occupato

rame $2*10^8$
fibra $3*10^8$

F -> Frame 
Ogni livello gerarchico processo le proprie unità dati
Pacchetto al livello 3
Frame al livello 2: oltre al header e al payload usa il CRC contenuto nella tail per rilevare eventuali errori

Tra il livello 2 al livello 1 il trasmettitore aggiunge una sequenza di bit all'inizio e alla fine, flag formata da 8 bit: 0 111 111 0
In idle il ricevitore legge tutti 1 o tutti 0, quindi quando riceve il flag il ricevitore inizia a sincronizzare il proprio clock in quanto sa che dopo lo 0 si deve aspettare 6 1 e poi lo 0.
A livello fisico dopo aver ricevuto lo 0, processo bit a bit gli 1 contandoli con un contatore, sia all'inizio che alla fine 

E' la flag di HTLC

Il ricevitore sa che la sequenza finale di flag non è il payload grazie al bit staffing che aggiunge nelle sequenze che corrispondono al flag uno 0 dopo 5 1 (il ricevitore aggiunge un delay di un bit)
Il transriver del ricevitore processa e toglie le flag all'inizio e alla fine, non arrivando quindi al 2o livello


Ritornando alla trasmissione
SE perdo l ACK, rinvio F dal buffer del mittente. Il destinatario capirà di avere gia quel frame nel buffer grazie al numero di sequenze nell'header, il sequence.
Il campo sequence è anche presente nell'ACK

Variabili di trasmissione
- $V(S)$: (mittente) indica qual è il prossimo frame da inviare. Lo incremento quando ricevo l ACK
- $V(R)$: (destinatario) indica qual è il numero di frame che si deve aspettare di ricevere. Lo incremento quando ricevo la sequence che mi stavo aspettando


Il protocollo per la correttezza lo mette al livello 2 quando so che il canale è molto inaffidabile 
Mettere HTLC al livello 2 costa molto in termini di tempo
Ora il tasso di errore del canale è diminuito, lasciando che se ne occupi il livello 4
Oggi usiamo un livello 2 affidabile sul canale radio e wireless 

Un protocollo insieme di regole che tiene sincronizzate due macchine a stati, in modo che evolvano in modo coerente

RTT Round Trip Time: tempo dall'invio di F all'arrivo dell'ACK

Svantaggi: è inefficiente a causa di $T_p$, è tanto piu inefficiente quanto piu aumenta il rapporto tra la lunghezza del canale rispetto a $T_x$
Utilizzo/efficienza della rete $U = {T_x \over (T_x + 2* T_p)}$
SE $T_p$ è piccolo, U tende a 1
SE $T_p$ è grande, U tende a 0

Appena ho mandato tutti i bit e sto aspettando ACK, posso gia mandare un altro frame, portando cosi U verso 1
k \* U 
k = o finestra di trasmissione / slamming window o numero di frame che il transceiver può trasmettere contemporaneamente 
La finestra tuttavia non è facile da dimensionare 

HTLC è un protocollo con trasmissione a finestra

SE il trasmettitore è abilitato a mandare piu frame, sono necessari piu buffer. 
Ci saranno almeno tanti buffer quanto è la dimensione della finestra

$figura1.26$ 
SE un frame N viene perso e mi arriva il successivo N+1, il ricevente non mando ACK del secondo, scartando cosi un frame corretto ma non nell'ordine corretto. Tutto quello che viene trasmesso dopo l'errore viene buttato
Fonte di inefficienza

HDLC per segnalare un errore, se lo rileva, può mandare un NACK (Negative ACK) del frame su cui è l'errore
NACK introdotto in modo tale che il trasmettitore si accorga dell'errore prima della fine del timer, rinviando il frame e risparmiando tempo

SE perdo ACK del tempo N, il ricevitore continua a ricevere i frame che vengono salvati, ma il mittente, quando non riceve l ACK del tempo N invierà nuovamente N ed i successivi frame che aveva gia mandato e che il ricevente aveva ricevuto corretti e conservato nei buffer 

NACK non piace perché è un messaggio di controllo in piu e perché non serve a molto inducendo un ACK con semantica selettiva 

Cambio di semantica:
ACK(N) dice che ha ricevuto correttamente fino alla sequenza N, quindi rimando ACK N invece di NACK N+1
Meglio un ACK cumulativo che un NACK selettivo
Vantaggio ACK cumulativo: dopo aver ricevuto il frame che prima era in errore (es N+1) poi manderò un ACK cumulativo molto superiore (es N+4)

Protocollo a finestra scorrevole di tipo GO BACK N: tecnica di trasmissione per protocollo a finestra scorrevole che prevede k buffer in $T_x$ e 1 buffer in $R_x$
(go back perche fino a n ho la sequenza giusta)

Protocollo a finestra scorrevole di tipo SELECTIVE REPEAT: ha k buffer in $T_x$ e k buffer in $R_x$
Avendo k buffer, conservo i frame corretti anche se non in ordine chiedendo poi selettivamente al trasmettitore di inviarmi nuovamente il frame specifico

TCP, lato trasmettitore BACK N mentre lato ricevitore SELECTIVE REPEAT


Campo sequence: numero di sequenza
Fisicamente è presente nell'header (in bit) MA quanto può essere grande una finestra a livello 2?
es 2 bit di seq, ho una finestra di 4 frame al massimo
in HTLC ci sono 4 bit di seq

MA se tutti i frame sono arrivati, MA tutti gli ACK non sono arrivati, allora verranno rinviati MA il ricevitore non riesce ad disambiguare il frame 0, non campendo se sia la vecchia o la nuova sequenza

MxSq (Max Sequence Number): data una finestra di trasmissione grande k, ho bisogno di k+1 numeri di sequenza 
La nuova finestra partira da k+1, poi 0 
es 2 bit di seq, ho MxSq = 4 e k=3
SOLO in GO BACK N mentre in SELECTIVE REPEAT serve 2k

4 bit seq --> al massimo 16 frame GBN --> finestra massima k=15
4 bit seq --> al massimo 16 frame SR --> finestra massima k=8

---

Consideriamo ora le reti di accesso, che hanno una topologia broadcast
Nel punto a punto, i nodi parlano in modo diretto ad un solo altro link 
Nel broadcast tutti sono collegati allo stesso dispositivo fisico, es hub o bus
L' hub non appena un nodo A trasferisce un messaggio verso B, l'hub propaga il messaggio a TUTTI i nodi collegati, anche al mittente
Prodotto un messaggio, tutti gli interlocutori ricevono quel messaggio

OSS nella topologia magliata per fare broadcast dovrei mandare tanti messaggi quanti sono i nodi MA tutti riceverebbero il messaggio piu di una volta

Avendo garanzia che tutti nodi possano fare un check sull'indirizzo destinatario, ho la certezza che il messaggio arrivi al giusto destinatario.

Ethernet è una rete broadcast.
Per la parte fissa, inizialmente è nata come bus lineare

Bus lineare: formato da un cavo coassiale, a cui si connettono i transiver di un nodo con un proprio cavo che tocca il mezzo conduttore interno 
SE A trasmette il suo segnale si propaga a dx e sx, raggiungendo tutti i nodi (secondo le regole di propagazione raggiunge tutti i nodi in momenti diversi in base alla loro distanza dal mittente)
Nativamente il messaggio è ricevuto da tutti i nodi


E' necessario gestire l'accesso mutuamente esclusivo al canale (che sia esso un centro stella hub o un bus) comune

Protocolli di accesso condiviso per reti broadcast
- Approccio deterministico: protocollo token-ring (ideato da IBM)
Viene eletto una stazione a master, (es con un algoritmo distribuito): essa conosce la composizione della rete e ne fa parte.
Il master genera un token e lo invia attraverso un anello logico (es prima A poi B poi C) passando il token con round robin
Ogni stazione è istruita in modo tale che invii i suoi frame solo se ha il token. 
SE una stazione con il token ha frame da inviare nel buffer, lo invia sul canale passando anche il token alla stazione successiva

La rete deve essere configurata nel caso si aggiungano nuovi nodi alla rete in modo da includerli nell'anello logico.

Problemi
- fairness: evitare che chiunque prenda il controllo del canale non ne approfitti
- Girando il token in modo sistematico, esso arriva a tutte le stazioni, incluse quelle che non hanno frame da inviare, perdendo cosi tempo.
- Caricando nel master la funzione centrale di generazione del token, nel momento in cui crasha la rete smette di funzionare e sarà necessario un reset

- Approccio "casuale": protocollo Ethernet
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
- MAC M Access Control: funzionalità di Carrier Sense, BEB, Collision Control
- LLC Logical Link Control: protocollo a finestra affidabile o meno 


Bridge
Supponiamo di avere una tratta Ethernet con tante stazioni, tanto che il tasso di collisione inizia ad aumentare. Troppe stazioni competono sullo stesso dominio di collisione
Con il Bridge dimezzo la probabilità di accesso al canale
Serve per separare domini di collisione, mettendo in contatto il dominio A con il dominio B

Il Bridge si occuperà di passera le frame destinate al dominio A dal dominio B e viceversa
Il traffico generato all interno dell'area A e B rimangono confinato se la destinazione è nella stessa area

A livello fisico il bridge ha un transiver e un MAC level proprio come una stazione qualsiasi, è un CSMA-CD

Requisito: che il bridge diventa egli stesso una stazione, quindi deve avere una scheda di rete

---

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


il livello 2 di Ethernet è composto dal MAC e dal LLC. 
A livello LLC sono interessato a ipotizzare la comunicazione da sorgente a destinatario
A livello MAC invece 
Ogni scheda ethernet ha un indirizzo MAC unico di 48 bit

Anche il livello 1 è composto da due livelli funzionali
- Livello Convergence: funzionalità di rete quali la trasmissioni dati, enable/disable della trasmissione, CS, collision detection (fisicamente queste funzionalità li fa il transiver, ma l'informazione deve essere passata al MAC)
- Livello physical medium-dependent : dipende fortemente dal mezzo che sto utilizzando


Problema: 3 stazioni su un cavo condiviso in contesa
A invia e B e C ricevono
B e C ricevono in modo asincrono ma è difficile da realizzare in quanto B e C devono attivare il clock di ricezione, dovendo quindi essere sincronizzato con quello del mittente MA non è dato sapere quando A trasmette

In banda base, SE trasmetto 3 1, il segnale rimane alto
In Ethernet invece i 3 1, viene garantito una transizione di stato da 1 a 0: codifica di Manchester
SE ho un 1: transizione da 0 a 1
SE ho uno 0: transizione da 1 a 0
La transizione avviene sulla meta del segnale, shiftato

ad ogni clock in ricezione leggo il canale di trasmissione
per estrarre il clock in ricezione: il livello fisico aggiunge 7+1 byte di preambolo nel messaggio, in modo che riesca ad estrarre il clock e fare diventare il proprio come quello estratto. In particolare 10101010101010 e poi 011
codificando manchester la sequenza di 1010... ottengo la stessa ma shiftata di mezzo colpo di clock, dando cosi la possibilità al ricevente, in base ai fronti della sequenza, di sincronizzare il proprio clock


Nella realta abbiamo diversi hub (o hub repeater) che concentra stazioni 
L'hub è comodo perche con un cavo punto punto (solitamente doppino telefonico) collego ogni stazione all'hub. Il dominio di collisione in questo caso avviene all'interno dell hub o tra gli hub

l'hub è un dispositivo di livello fisico, quindi si comporta come totalmente broadcast
il controllo di accesso è sempre nella singole stazioni, l hub semplicemente trasmette a tutti i transiver ciò che riceve 

Oggi la gran parte delle reti Ethernet è fatta con questa topologia

il protocollo specifica anche il clock


MA tutto quello che abbiamo fatto finora è per una rete a 10Mbit, se vado a 1Gbps?
Cambia la dimensione minima del pacchetto perche cambia $T_x$, in particolare a 512 ns MA $T_p$ non è cambiato e quindi il protocollo non rileva le collisioni
Nello standard sarà necessario cambiare la dimensione minima del frame, in particolare sarebbero necessari 50k bit, diminuendo U moltissimo (es segnale di ACK). 

Un altra soluzione è quella di cambiare il mezzo
La soluzione migliore è diminuire L, la lunghezza totale del canale

Diminuendola da 2.5km a 25m (da nodo ad hub), quindi 25 andata all hub, 25 al nodo, 25 di ritorno da nodo destinazione e altri 25 per tornare al nodo destinazione
$$2*T_p = {10^2 \over {2*10^8}} = 0.5 \micro s$$

Usiamo un compromesso
- 200m di L massimo -> 2$t_p$ su 800m -> 2$t_p$ = 4 microsecondi
- taglie minime di frame a 512Byte. Ho un padding duplice: uno che lo fa fino a 64B ma poi il mio livello fisico aggiunge 512-64 Byte 

Inefficienza


Soluzione alternativa: ha forzato la transizione tra bridge a switch


Tornando sul bridge
Bridge separa i domini di collisione
MAC solo presente nei nodi e nel bridge tra gli hub
quindi a bordo del bridge ci devono essere tante schede quanti domini di collisioni voglio avere 

il bridge ha una tabella di forwarding che contiene, data una stazione, in che dominio si trovano, quindi in che porta dovra usare
ATT il bridge non si deve comportare come un hub, ma deve fare store and forward 
SE arriva un frame in cui mittente e destinatario sono nella stessa porta, il bridge butta quanto ricevuto

Problema della gestione della tabella: fa learning e se non sa dove sia, fa broadcast MA senza rimandare sulla linea in cui ha ricevuto (tecnica di fladding)
velocita di learning data dal traffico

Casi limite: aggiunta di un nuovo nodo o cambio di hub a cui era collegato il nodo. Nell'ultimo caso il bridge non lo propaga perche ha una tabella di forwarding sbagliata. Viene quindi introdotto un TTL Time To Leave ricominciando il learning 

---

ATT ERRORE NEL BEB = 0 - 2^i -1
-1 perche nel caso ci sia una sola collisione ...

Il concetto di indirizzamento c è a quasi tutti i livello (1, 2, 3, 4) ognuno con un proprio indirizzamento
- Livello 2: MAC address
- Livello 3: IP
- Livello 4 Port address


Perche fare come il bridge per il broadcast sarebbe sbagliato? Dato che la scheda con CS e collision detection, non saprà mai se avra colliso

Termine forwarding: processo in grado di trasferire unita dati da una porta di ingresso a una porta d uscita
Il "forwarding" dal routing invece è che la tabella su cui faccio forwarding non è costruita solo in base alla rete locale, ma dalla conoscenza della topologia di tutta la rete


Switch
Differenza col bridge è che NON c'è CSMA/CD ma c è un cavo dedicato dal nodo allo switch, quindi non ci saranno mai collisioni
Sono quindi grandi accumulatori anche a grande velocita in quanto non ci sono vincoli di distanza
Porte pero limitate a 32
Spesso vengono collegati sia ai router che ad altri switch

Essendoci compatibilità con le frame posso sostituire in qualsiasi momento un bridge con uno switch
In realta il CS verra sempre fatto ma non ci saranno mai collissioni
Viene anche mantenuto la dimensione minima del frame anche se non serve

In realta sto aggiungendo complessita nello switch che dovra gestire molte linea a grandi velocita

Fast Ethernet NON STUDIARE


A livello 2 VLAN Virtual LAN
Aggregazione delle stazioni in gruppi omogenei
Due stazioni di due gruppi diversi non possono comunicare
E' uno strumento organizzativo molto utilizzato

Per poterla realizzare è necessario modificare il bridge in modo tale che nel processo di learning, impari anche il gruppo della stazione. 
Inoltre è necessario cambiare le schede di rete delle stazioni in modo che includa anche il colore del gruppo a cui appartiene

Standard IEEE 802.1Q
Viene usato davvero il colore come discriminante tra i gruppi

il frame del VLAN utilizza il campo gia esistente lunghezza che in realta dal protocollo è previsto essere anche type
Il campo type per le frame 802.3 è 8100 in esadecimale, caratteristica di essere superiori a 1500
Altrimenti si sa che si sta lavorando con la VLAN, aggiungendo dopo 2 byte per il colore 

Opinione del Rossi: se cambia volendo una VLAN, dovro aprire il mio dispositivo, cambiare la scheda di rete per tutti i device, rischia di diventare oneroso

Solitamente si prende uno switch non cambiando la scheda delle singole stazioni, lavorando solo sullo switch, taggando le porte a configuration time 
Permetto alle stazioni di generare traffico untagged e appena arriva allo switch si ha il tag


switch to switch viene chiamato trank, in questo caso passano frame di qualsiasi colore e sara lo switch destinatario a gestirlo

(finendo il livello 2 ho gia fatto 1/5 del programma, RIP)
es
10km, 100Mb, U=50%, F=?
U= tx/tx+2tp
0.5\*(tx+2tp) = tx
tx = F/D
F=tx \* D

0.5 (F/D + 2tp) = F/D
tp=0.5F/D
2D tp = F
F = 2 \* 10^4 \* 10^4/2\*10^8  = 10^8 \* 10^-4 = 5 \* 10^-5

(ES UGUALI A QUELLI SU ARIEL)

RISSUNTI FINE

dal livello 3 in su è dell'host
il livello 1 e 2 riguarda invece la rete 

al livello 3 abbiamo 2 funzioni
- Addressing: indirizzo numero per indentificarsi. Consente di indirizzare dei dispositivi remoti alla rete
- Rowting / instradamento: cammino migliore per raggiungere la destinazione

Ci sono delle code di input, delle code di output
input: unita dati del livello 3: pacchetti
Processo di forwarding: metta input in output in base a una tabella in cui per ogni destinazione esiste una linea di output. Tabella popolata non solo con le destinazioni della rete ma con tutte quelle di Internet
Questo è possibile grazie al processo di rowting che raccoglie dati, li processa, e popola le tabelle di rowting. E' necessario che abbia conoscenza della topologia di rete grazie alla quale popola la tabella 


---

Moduli logici:
IP: Addressing
OSPL: Routing
Problema: dato un indirizzo destinazione, dobbiamo capire quale sia il cammino migliore per raggiungere tale destinazione

Addressing
Indirizzo IP vale su tutta la rete internet a differenza di MAC
Caratteristica: indirizzo unico su tutto il pianeta
unita dati L3: pacchetto

- Total lenght su 16bit
- TTL Time To Live per 
- Source IPv4 su 32bit
- Destination IPv4 su 32bit
- Option
- Payload

IPv6 invece ha 128bit

Problema frammentazione: se ho un host con TCP che produce dati da 7000B MA devo farceli stare su un token ring che li fa passare su 4kB e magari nella lan destinazione ne fa passare al massimo 1kB

Deve frammentare i 7k in 4k e 3k (non viene frammentato in questo modo)
Bisogna tener presente che al payload bisogna aggiungere gli IP delle due macchine e altre info che in totale pesano 20B.
Il IP non gestisce una byte stream: si utilizza un fragment offset su 13bit MA la lenght è su 16bit. L'offset non viene contato sui byte ma sugli ottetti
QUINDI la dimensione deve essere un multiplo di 8
nel nostro caso è 3976 

MID = 0 SE il frammento è l ultimo del pacchetto

| Nome         | PKT ID | Fragment Offset | Tot length | Dati  | MID |
| ------------ | ------ | --------------- | ---------- | ----- | --- |
| 1° pacchetto | 20     | 0               | 7000B      | 3976B | 1   |
| 2° pacchetto             |  20      |  497               |  7000B          | 3024B      |    0 |

Frammentazione dei due pacchetti per la seconda rete nel router del destinatario

| Nome         | PKT ID | Fragment Offset | Tot length | Dati  | MID |
| ------------ | ------ | --------------- | ---------- | ----- | --- |
| 1° PKT 1a PT | 20     | 0               | 7000B      | 1480B | 1   |
| 1° PKT 2a PT | 20     | 185               | 7000B      | 1480B | 1   |
| 1° PKT 3a PT | 20     | 370               | 7000B      | 1016B | 1   |
| 2° PKT 1a PT | 20     | 497               | 7000B      | 1480B | 1   |
| 2° PKT 2a PT | 20     | 682               | 7000B      | 1480B | 1   |
| 2° PKT 2a PT | 20     | 807               | 7000B      | 64B | 0   |

Note: 
- Dati: 1480B (numero piu vicino a 1500-20 e divisibile per 8)
- Fragment Offset: 185 (=1480/8)

Chi ricompone i due frammenti IP: la destinazione, in particolare l'IP del destinatario
Vantaggio: non sovraccarichiamo i router intermedi

Nel caso di perdita del segmento, l IP se ne accorge 
E' il TCP che nel caso ritrasmetta i dati MA rimanda tutto, non solo quello che manca perché è il livello 3 che sa quale non è arrivato

In Internet il livello 2 non fa cose affidabili dal punto di vista prestazionale, delegandolo a livello 4

I 32 bit del campo IP address
- Cosa contiene
Ogni rete in internet ha un NET ID. Ognuna delle quali ha delle macchine interconnessi, ognuna delle quali ha un host ID
La gerarchia è utile per i router intermedi di rete che non devono quindi ispezionare tutti i 32 bit, ma SOLO il NET ID
Grazie alla gerarchia nelle tabelle di instradamento dei router intermedi conservo solo i NET ID

- Divisione in classi: 
- Unicast
	- Classe A: 7 bit per NET ID e 24 bit per Host ID
	- Classe B: 14 bit per NET ID e 16 bit per Host ID
	- Classe C: 21 bit per NET ID e 8 per Host ID
- Multicast: Classe F: 28 bit per Multicast address
- Reserved: Classe E

255.255.255.255 per indicare tutti gli host
192.16.8.0 = 11000000.00010000.00001000.00000000

Problema: spreco di indirizzi
Soluzione: subnetting
- Subnetting
NET ID - SubNET ID - Host ID
L'organizzazione in subnet non è definita da uno standard, ma è demandata al livello IP che sceglie quanti bit degli host ID demandare al subnet ID
Per discriminare SubNet e host id, aggiungo ad ogni entry nella tabella di routing la SubNet Mask, tanti 1 quanti bit sono usati dal SubNet ID. Facendo l'AND tra il mio indirizzo e la mask, maschero i bit dell host id
es 16bit NET ID - 6bit SubNet ID - 10 Host ID
11111111 11111111 111111 0000000000 = /22 cioè ha bisogno di 22 1

130.50.15.6
xxx . xxx . 000011 11.00000110
111..111. 111111 00.00000000

Come risultato rimarranno solo i bit del SubNet: 000011 = SubNet ID 3

Quindi: 
- Viene analizzato il NET ID
- SE è lo stesso della rete a cui è collegato il router, manda li il pacchetto
	- Viene controllato il SubNet ID
		- Viene controllatol Host ID

Svantaggio: complica le tabelle di routing

- CIDR Classless Inter Domain Routing
Sono state scartate le varie classi
A varie organizzazioni vengono dati una certa porzione di indirizzamento libera
ogni entry nei router dovra avere un indirizzo di partenza e una maschera che filtrera i bit di host ID

---

es Tabella di instradamento

| Location | IP inizio    | IP fine      | Tot indirizzi | Base                                    | Maschera |
| -------- | ------------ | ------------ | ------------- | --------------------------------------- | -------- |
| Milano   | 194.24.0.\_  | 194.24.7.\_  | 2048          | 1100 0010 0001 1000 0000 0000 0000 0000 | \\21     |
| Roma     | 194.24.16.\_ | 194.24.31.\_ | 4096          |                                         |          |
| Torino         | 194.24.8.0             | 194.24.11.\_             |   1024            |                                         |          |

Maschera \\n = n bit a 1 e 31-n bit a 0

Arriva pacchetto con indirizzo 194.24.17.4
SE applicando la maschera all'address ottengo l'indirizzo base della location, l'indirizzo appartiene a tale rete
Prova a mappare l indirizzo su Milano
1100 0010 0001 1000 0001 0001 0000 0100 base
1111 1111 1111 1111 1111 1000 0000 0000 maschera
1100 0010 0001 1000 0001 0000 0000 0000 base AND maschera

Non ottengo la base di milano
Facendo la stessa cosa con Roma, ottengo l'indirizzo base di Roma
Il pacchetto viene quindi instradato verso il SubNet di Roma

Le tabelle di routing contengono quindi l'indirizzo base, quanti bit utilizza la maschera, la maschera stessa MA l'elaborazione della tabella è piu costosa in quanto devo potenzialmente scorrere tutte le entry per trovare il SubNet giusto

CIDR ha liberato molto indirizzi IPv4

Vantaggio vero dell IPv4: 
- NAT Network Address Traslation 
Dispositivo (router) che si occupa di tradurre indirizzi
Separo internet con il NAT da un insieme che è in grado di concentrare un numero elevato di macchine
Gli Host non utilizzano un indirizzo IP pubblico MA un indirizzo IP privato
L'indirizzo pubblico è unico al mondo mentre quello privato è assegnato dall'amministratore della rete locale
Quando un Host della rete deve comunicare attraverso Internet, dovrà utilizzare un indirizzo pubblico trasformando il proprio indirizzo privato a pubblico attraverso il NAT

10.0.0.0 - 10.255.255.255
...

Basta un indirizzo IPv4 pubblico per rappresentare centinaia di dispositivi privati

es 
host: 10.0.0.1 
NAT: 194.24.16.0
Server: 200.10.0.0

Tabella NAT

| IP sorgente | IP NAT      | IP destinazione | # Porta Sorgente | # Porta destinazione |  Porta NAT   |
| ----------- | ----------- | --------------- | ---------------- | -------------------- | --- |
| 10.0.0.1    | 194.24.16.0 | 200.10.0.0      | 10               | 80                   |10     |
| 10.0.0.4    | 194.24.16.0 | 200.10.0.0      | 15               | 80                   | 11    |

Identificatore logico ricavato dal livello 4 
TCP comunica con i processi applicativi grazie alla porta logica, un identificatore numerico univoco logico all interno della macchina
La porta logica è l'"indirizzo" del livello 4, viene salvata nell header di TCP
La porta è un descrittore di socket

Da standard quindi il livello 3 guarda l header del livello 4
Avra bisogno di avere anche una maschera del livello superiore

Porta destinazione 80 = Internet

MA se due macchine usano la stessa porta sorgente non funzione. Il NAT crea quindi un altra entry in cui è il NAT che da il numero di porta sorgente, evitando quindi sovrapposizioni

Lato destinatario: per aprire il mio sito all esterno, apro la porta di servizio 80 sull'indirizzo del server

Problema: Access Gateway non conosce il MAC address della macchina destinataria, o in generale su una rete che instrada con un indirizzamento diverso
Soluzione: 
- ARP Address Resolution Protocol 
Risolve un indirizzo IP in un indirizzo MAC mandando un ARP request in broadcast e la macchina destinataria rispondera con una ARP reply (ma essendoci specifica l IP address, solo la macchina giusta rispondera) 
Sara conservata una tabella con un time to leave in cui vengono salvati gli IP e il MAC address

SE ho piu LAN interconnesse, vi è il Proxy ARP nella macchina (per forza un router perche serve che lavori a livello 3) che collega le due LAN cosicche quando riceve l'ARP request propaga la richiesta (se il SubNet ID è il suo) e risponde specificando pero il MAC address del proxy

RARP Reverse ARP


formato pacchetti 802.3

| Campo            |  Bytes   | Note    |
| ----------- | --- | --- |
| DA          | 6   |     |
| SA          | 6   |     |
| Type/lenght | 2   | 0806 = ARP    |

formato pacchetto ARP 

| Campo                               | bit |     |
| ----------------------------------- | ----- | --- |
| HW type                             |  16     |     |
| Protocol Type                       |    16   |     |
| ...                                 |       |     |
| Operator                            |      16 |     |
| Sender HW address | 16      |  MAC del gateway   |
| Sender IP address                   |   16    |     |
| Target HW address                   |     16  |     |
| target IP address                                    |  16     |     |


Figura 6.26
Problema: macchine che entrano nella rete locale, non portandosi dietro l IP address dell organizzazione precedente. 
Gli IP non sempre sono assegnati statisticamente
IP vengono assegnati dinamicamente con DHCP Dynamic Host Configuration Protocol
Devo ovviamente garantire che l'IP che assegno dinamicamente rimane unico per il periodo di utilizzo
Le macchine si rivolgono automaticamente al server DHCP della rete, solitamente il gateway della rete

Nelle organizzazioni piu complesse, ci possono essere diversi DHCP server 

- Protocollo DHCP
Il client fa una richiesta, DHCP Discover. Campi: IP sorgente (0.0.0.0), IP destinazione del DHCP server (255.255.255.255), TID transaction ID (generato dal client)
Il server associa MAC address - TID, mandando una DHCP Offer che manda al client. Campo: IP Sorgente (IP Server), ..., TID
Per verificare che IP address non sia gia in utilizzo dagli altri, il server fa un ping con l IP address che sta offrendo
Il client prende atto dell offerta, potenzialmente piu di una (se ci sono piu server).
Il client produce una DHCP request. Campi: IP Sorgente (0.0.0.0), IP Destinazione (IP Server sempre in broadcast), TID
Da quel momento in poi al client è assegnato quell IP, il server manda quindi un DHCP ACK
Da quando ricevo ACK il client diventa indirizzabile MA prima il client fa check attravero un ARP request (non dovrebbe rispondermi nessuno)

DHCP funziona a 4 vie (Discover-Offer-Request-ACK) perche i server sono piu di uno

Vengono inseriti controlli per la discover e la request, ripetendo nel caso la ritrasmissione per al massimo k tentativi

---

ICMP Protocol (livello 3)
Si occupa della rilevazione degli errori, verifica la raggiungibilità (server utilizzano ICMP per verificare che l IP che si vuole assegnare non sia gia utilizzato), controllo di congestione (trasmette chock packet che segnalano verso i nodi vicini, la situazione congestionata del nodo in modo che venga evitato quel nodo), misura prestazioni...

| Message type            | descrizione |
| ----------------------- | ----------- |
| Destination unreachable |             |
| Echo request            |             |
| Echo reply              |             |
| Timestamp request       |             |
| Timestamp reply         |             |
| ...                        |             |

figura 6.31


Routing
Nel router abbiamo una coda di ingresso per ogni porta di I/O e una coda di uscita per porta porta di I/O
I pacchetti vengono processati da un processo Forwarder e smistati nella specifica coda di uscita, scegliendo in base ad una tabella che in base ad un indirizzo IP destinazione, viene indicata una porta di I/O
Avro tante entry quante sono gli IP conosciuti

IP della sorgente è necessaria ma utilizzata solo dal destinatario

Processo di routing popola la tabella 
è asincrono rispetto al processo di Forwarding
Vediamo il router diviso in 2
- piano dati
- piano controllo

Il processo di routing deve avere una certa conoscenza di tutta la rete in modo tale da costruirsi il cammino minimo anche se nella tabella non troviamo tutto il percoso ma solo il successivo nodo da raggiungere per raggiungere l IP destinazione
Per il cammino minimo come metriche utilizzeremo il delay e il numero di hop 

Il forwarder fa la stessa cosa del Bridge (invece del MAC c è l IP)


Come costruire un processo che fa routing
- DV Distance Vector
- LS Link State

DV
Protocollo RIP
I vari router si scambiano dei vettori di distanze. Con distanza intendiamo la metrica che vogliamo utilizzare come costo per raggiungere un nodo

I costi dei link sono derivanti da un ICMP 
Ipotizziamo che i costi rilevati siano omogenei dai nodi collegati

nelle code di I/O oltre al traffico ci sono anche i pacchetti di controllo del processo di Routing
Tabella nei routing osno chiamate tabella di adiacenza in quanto con gli echo scopre i costi solo dei nodi adiacenti

Vettore delle distanze viene propagato ai nodi adiacenti in modo da trasmettere la conoscenza della rete, inizialmente cio che c è nella tabella di adiacenza (gli indirizzi dei nodi ed i costi associati MA non si dice il link utilizzato in quanto è un info locale inutile)

Ricevendo il distant vector, il nodo scopre nuovi indirizzi raggiungibili (senza comprenderne la topologia) e capisce quanto costa arrivare ai nuovi indirizzi e quindi aggiugendo una nuova entry nella tabella di routing, dato dall indirizzi e dal costo uguale alla somma tra il costo nel distant vector e il costo per raggiungere il nodo da cui proviene il distant vector 
Il diametro della rete influenza il tempo con cui si viene a conoscenza degli indirizzi da un nodo
La conoscenza si diffonde in base al diametro della rete

Quando per un entry gia esistente, si ottiene un costo minore, si cancella la entry e aggiorna costo e link.
E' quindi anche migliorativo

Il Distant Vector viene mandato periodicamente MA l'invio non è sincronizzato tra i link (ed è meglio cosi)
Quindi non è detto che le tabelle di routing convergano immediatamente per il cammino minimo

Problema: errore/guasto in un link
Con il ping periodico viene rilevato il guasto, assegnando un costo infinito (in realta un valore intero massimo che indica infinito)
L'informazione viene quindi propagata attraverso il DV
SE pero un altro nodo A propaga il DV prima che il nodo B mandi il DV con il costo infinito, allora viene rilevato che A riesca a raggiungere il nodo con un costo minore di infinito, e B cambia la sua entry creando un loop in cui il pacchetto rimbalza tra i due nodi (bouncing effect)
Quando ad A poi arrivera DV di B, A aumentera il costo continuamente perche rileva che il costo da B alla destinazione è aumentato (count to infinity)

Questo limite del DV è generato dalla mancanza di sincronizzazione e dalla perdita ...

In realta il bouncing effect si fermera prima dell infinito grazie al raggiungimenro del nodo da un altro nodo

Soluzione: split horizon 
Convenzione che prevede che ogni nodo quando propaga il proprio costo per una destinazione, propaga il costo reale su tutte le adiacenze che non intende usare per raggiungere la destinazione mentre infinito sulle adiacenze che intende utilizzare per raggiungere la destinazione 


Protocollo RIP: implementazione del DV
RIP usa una policy triggered update: ogni nodo la usa tutte le volte che rileva una destinazione tra le adiacenti non raggiungibili mettendo nella propria tabella la entry a infinito. INVECE di aspettare la scandenza di timer per la ritrasmissione del DV, il DV viene mandato immediatamente 
Come metrica RIP utilizza hop count
L'infinito è >16 (non si utilizza quindi RIP per reti con diametro maggiore di 16)
Usa un random per il trigger, tutte le volte che rilevo un costo infinito non faccio un update instantaneo ma aspetto un tempo casuale per evitare storm the ...


LS
Protocollo OSPF Open Shortest Path First
Gran parte di internet è OSPF

---

Link State Routing
1. Costruzione adiacenza
Le tabelle di adiacenza avviene nello stesso modo del DV 

2. Diffusione LS
Una volta misurato il costo delle diacenze
Questa informazione non viene propagata ai nodi adiacenti, MA a tutti i nodi della reta

Questo viene fatto con il Floodind: evoluzione del broadcast che permette di propagare in un unica direzione 
Flooding viene implementato in modo che i nodi che ricevono le info di un nodo A vengono inviate in tutti i link di uscita tranne quello in cui l ho ricevuto
Ogni nodo appena riceve un LS da un nodo adiacente, manda un segnale di ACK. Questo cerca di garantire la consistenza. SE non ricevo l ACK, viene ritrasmesso il LS (ridondanza locale) ma non viene rinviato all infinito in quanto sappiamo che nelle altre direzioni verra ripropagato (ridondanza temporale)
Creo inevitabilmente dell overhead, della ridondanza di alcune info

SE ho N nodi, ho N^2 messaggi che girano

LS composto da: Sorgente, Sequence, TimeToLive, NumeroHop, 
Sequence: assegnato dalla sorgente che permettono di evitare le coppie di LS gia ricevuti

Inondando la rete di traffico di controllo TUTTI conoscono esattamente la topologia della rete
Questo ci permette di superare il problema dei DV, count to infinity

LSR 
Per ogni link ho un costo bidirezionale

OSPF Open Shortest Path First
Algoritmo che ogni nodo della rete esegue tutte le volte che riceve un update di un LS
in particolare usa l algoritmo di Dijkstra

Maggiore flessibilita
Convergenza sicura
MA pago in traffico e costo computazionale

Come ragiona un nodo
Livelli di tabelle
- Tabella di adiacenze che popolo attraverso le ICMP
- Tabella di routing
- Tabella NET ID

Uso combinazione routing (guardo le 3 tabelle) e forwarding (faccio un hop)

Architettura di rete OSPF: topologia che prevede un area0 / backbone (OSPF) collegate ad altre sottoaree (RIP / OSPF). NON ci sono collegamenti tra sottoaree

SE aree0 molto grandi, avremo grandi costi di traffico e computazione
Un nodo viene eletto come Designated Router per fare OSP in modo che il costo computazione sia centralizzato. QUINDI tutti i router della rete non si scambiano in flooding ma mandano i LS solo al Designated Router
Il Designated Router propaghera poi le tabelle specifiche per ogni nodo
Problema di vulnabilita della rete: il Designated Router viene duplicato per sicurezza
Problema di convergenza del traffico verso il Designated Router: i link verso il Designated Router devono essere robusti e veloci 

Oggi si sposta la funzione di rounting all interno di un datacenter (SDN SW Defined Networking)
In questo modo disaccoppio piano dati e di controllo. I nodi fanno solo forwarding
OPEN FLOW: protocollo che regola la comunicazione tra ogni apparato di rete e il "datacenter" associato

Internet: collezione di AS Atonomous System
Le varie aree0 sono collegate a Internet Backbone (pochi nodi ad altissima velocita; protocollo BGP)
Tier 1: Internet Backbone
Tier 2: AS
Tier 3: reti di accesso / reti periferiche


BGP Border G Protocol = Path Vector
Assomiglia a DV
Vengono propagati vettori delle distanze senza fare flooding.
In questo caso i DV contengono anche per ogni destinazione, il costo e il cammino per raggiungere la destinazione (per evitare count to infinity)

Costo inferiore del LS
MA i nodi devono conoscere il Path a configuration time o run time
BGP funziona SOLO tra router di Tier 1


I router devono rispettare i QoS
Oltre ai pacchetti con il payload ci sono anche pacchetti di controllo 
Il resto dei pacchetti va nel flusso dati
Estratto il packet classifier (TOS bit) dall header, viene fatto uno scheduling sulla coda in base alla politica di scheduling

Il classifier decide in quale coda inviare il pacchetto
Le code di I/O per ogni porta di I/O sono diverse in base alla qualita di servizio che vogliono offrire
Un router ha tante code quanti sono i servizi che puo offrire


| Tipo di traffico - Esigenze  | Affidabilita | Delay | Jitter | Banda |
| ------------------ | ------------ | ----- | ------ | ----- |
| email              | Alta         | Basso | Basso  | Basso |
| web (come FTP)     | Alta         | Basso | Basso  | Medio |
| FTP                | Alto         | Basso | Basso  | Medio |
| audio streaming    | Basso        | Medio | Alto   | Basso |
| video streaming    | Basso        | Alto      | Alto       | Alto      |
| Internet telephone | Basso        |       |        |       |
| video conference   | Basso        | Alto      | Alto       | Alto      |

Jitter: tempo da quando il messaggio parte a quando arriva al destinatario
NON tutti i pacchetti hanno lo stesso ritardo

La digitalizzazione di un segnale analogico passa da campionamenti. Decido una frequenza di osservazione e ad ogni bit campione il valore di tensione, producendo un byte 
Piu è la frequenza di campionamento maggiore è la qualita


8000 campioni al secondo ( uno ogni 125microsecondi) per garantire...
Dato che ogni campione produce un byte, al secondo produco 64KB (minimo di banda per avere una qualita minima). Alternativa 16000 campioni al secondi quindi 128KB
PCM Pulse Code Modulation
Anche in ricezione dovro avere la stessa frequenza di arrivo dei messaggi, quindi uno orgni 125microsecondi (CBR Constant Bit Rate in ricezione)

Anche perche audio e video hanno un Jitter sensibile
Per garantire questo requisito su Internet, viene delegato al SW: Buffer di playout, permette di bufferizzare e risolvere la scarsa qualita della rete (dimensionamento in base alla qualita della rete)


La coda di output dei router è gestita con due blocchi
- Servizio affidabile: solitamente pacchetti generati dal TCP
- FIFO
Questa coda viene gestita con un algoritmo di scheduling FIFO
Problema della provenienza

SE TCP rileva traffico intenso, potrebbe droppare tutti i pacchetti in arrivo nella coda.
MA poi quando viene rispreso il traffico, ci sarebbe ancora un brust di pacchetti 

- RED Random Early Detection
Cerco di prevenire l insorgenza del problema di traffico a burst
Vnegono prese due soglie
- MIN Thrashold
- MAX Thrashhold
Viene definita una LengthAverage
LAVG = alpha^LOLD + (1-alpha)\*LCURRENT
0.5 < alpha < 0.8

Quando arriva un pacchetto, guardo SE la LengthAverage è sotto la min, in tal caso accodo mentre se è sopra la max, allora scarto
SE è tra le due soglie accodo secondo una probabilita p

Droppo casualmente pacchetti in coda
Droppando pacchetti anche se il nuovo pacchetto ci starebbe nella coda, permette di evitare preventivamente il problema del traffico a burst


- Servizio sensibile al delay (UTP)
WFQ Waited Fair Q
SE voglio differenziare le code in base a diverssi livelli di sensibilita del delay, associo ad ogni coda un peso, l equivalente della frazione di canale che assegna al traffico
Scheduling con round robin

(wi / somma k wk) \* RateDisponibile
peso della coda / totale pesi * Rate

es 
con i=1 a 4 wi=4, 2, 2, 2 peso della coda
w1 = 4/10 = 2/5 R
w2,3,4 = 2/10 = 1/5 R

SE canale è da 1Mbps, a w1 assegno 500kb e a ognuno degli altri 125kb
w1 si svuotera prima delle altre code


Non discrimina secondo il Jitter o il delay richiesto
Tiene conto anche della lunghezza dei pacchetti, restando Fair: ad ogni pacchetti viene dato un timestamp in funzione della categoria e ...
Le code vengono schedulate in base a tale timestamp


SE un router gestisce una coda come WFQ, la slice del canale è determinato dal peso
Alcuni router (solitamente di accesso) fanno shaping, cioè se viene dichiarato all ingresso 1/4 del canale viene verificato se viene prodotto effettivamente 1/4
Tecnica token bucket: ho un timer che mi determina la Rate in base alla quale rempio il bucket di token. Qualsiasi quantita di dati la sorgente generi, dalla coda prendo il pacchetto SOLO se c è un token nel bucket
SE finisco i token, sto andando a una Rate superiore a quanto dichiarato

La coda che va in overflow eventualmente sara quella di input


Tunneling
Dato un Host che lavora su una rete IP e un altro host che lavora su una rete IP, SE le due reti sono collegate da una rete NON IP, non posso mandare l IPHeader e l'IPPayload
Il Tunneling consente di creare un tunnel NON IP che permette di trasportare, senza modificarlo, il pacchetto IP originale, incapsulandolo in un pacchetto IP, aggiungendo l'header della rete.

Ovviamente la rete NON IP dovro sapere la corrispondenza dell IP destinazione rispetto all'indirizzo del gateway destinazione



Nella realizzazione delle aree0 si richiede l efficienza dei router
Tecnica MPLS Multi Protocol Label Switching utilizzata nelle aree0
Si ragiona attraverso le etichette, sovrapponendosi all indirizzo IP, MA che vale solo all interno del singolo router
Lo switching lo avevamo conosciuto a livello 2, mappando una porta di ingresso in una di uscita

MPLS agisce sulla parte del router che si occupa del forwarder, facendolo operare come uno switch
Trasformo il router in un apparato che fa forwarding SENZA curarsi del routing

il LS continua ad essere a bordo del router, MA è funzionale a far funzionare il router come uno switch
Il router di gateway dell area0 si chiamano Area Border Router: qui si compie la trasformazione da LS a MPLS


Router non convenzionale (MPLS)
OSPF è ancora li
differenze:
- le informazioni di routing popolano anche la Label switching table
- l'IP header e l'IP payload vengono trasformati in un MPLS pacchetto. Questo avviene tramite tunneling, incapsulando quindi il pacchetto IP
- labeling: assegnamento della label al pacchetto
- Gestisco le code in base all etichetta

Il ruoter ragiona solo in base alla porta di ingresso - etichettaRilevata - etichettaNuova - porta di uscita. Ci sara una tabella per ogni porta
l'unica cosa che si porta dietro per tutta la rete sono i QoS

Le tabelle inizialmente NON sono vuote, ma i router si ritrovano le tabelle gia costruite da un processo centralizzato (forma di designated router)

MPLS formato pacchetto
l'header di MPLS contiene
- label su 20bit
- CoS Class of Service 
- TTL time to leave

In questo modo otteniamo aree0 il piu veloce possibili perche non si deve ispezionare l IP MA viene fatto tutto piu velocemente come se fosse uno switch



BGP funzionalmente è a livello 3 MA in realtà nell'implementazione è un protocollo a livello 7 utilizzando TCP

---

Spanning Tree
Costruire l albero dei cammini minimi per fare oltre la comunicazione punto-punto, ma anche il broadcast (facile su CSMA-CD MA non su una rete magliata)

NO ALGORITMO

Per lo spannign tree devo avere rete con OSPF che ci permette di raccogliere i costi e formare le tabelle in ogni nodo
Un router root nello spanning tree viene eletto come root (un modo è eseguendo un algoritmo di elezione o dall indirizzo inferiore) 
Ogni nodo definisce le porte di output che permettono di raggiungere le destinazioni
RootPort se i nodi sono sui rami  cioe sono sul path per le foglie

Come evitare i loop: se due porte hanno lo stesso costo, sceglie etichetta inferiore


IPv6
Abbiamo come min 40Byte per l header
Address da 16 byte l uno

Notiamo la divisione quasi geografica anche nel pacchetto
TLA -> NLA -> SLA

Upper bound del payload sempre di 64K
ToS rinominato in TrafficClass consente di classificare in base alle qualita di servizio richiesto mentre FlowLevel viene inserita dalla sorgente al proprio specifico flusso dati

NextHeader contiene l header di TCP di default
SE è invece un header diverso da quello TCP, vuol dire che è uno di quelli previsti dello standard
- Step by step (0)
- Source routing (43) (al massimo posso specificare 24 indirizzi nel campo opzione, quindi 48; avro poi un array di 24 bit che è 0 SE l IP deve essere raggiunto in modo approssimato mentre 1 in modo esatto)
	- Esatto
	- Approssimato

Notare che mancano i campi per la frammentazione, ma viene inclusa nella option


Come far interagire macchine IPv4 e IPv6
- Mettere un gategay v4-v6: PT ProtocolTransformation per trasformare un header in un altro header. Il NAT mappa da v4 a v6 e viceversa grazie a un pull da cui preleva degli IPv4/v6 da assegnare


Domande esame
- Quali paccheti in piu vengono mandati in un LS? Deve essere inviato anche un ACK e per ogni nodo faccio fludding
- Quali informazioni sono presenti in un LS e NON in un DV? Nel LS è presente anche la conoscenza della topologia della rete grazie al fludding
- Dovendo scegliere tra uno schema GoBackN e uno Selective Repeat quali elementi considero? Considero la memoria lato ricezione del buffer e preferisco Selective Repeat quando ho un collegamento instabile (Parametri: Memoria disponibile e canale affidabile)
- ARP: come ci si comporta nel caso la macchina destinazione NON appartiene alla stessa rete di quella sorgente? Sara necessario un proxy ARP il quale essendo collegato alla LAN riceve il broadcast ed essendo di livello 3 capisce che la destinazione è in un altra rete (grazie al NetID) propagando la ARPrequest e risolvendo il problema facendo una reply con il proprio MAC

---

...

---

TCP/IP
TCP è al livello di trasporto, affidabile: deve essere consegnato tutto in ordine

header: (foto del libro antiquata)
- porta sorgente 16bit: scelta dall Host (solitamente >1000 perche sono per lo user)
- porta destinazione 16bit: porta nota 
- Sequence number 32 bit: indica l inizio dei byte che vengono trasmessi in un segmento TCP
- ACK number 32 bit: identifica il byte successivo che mi aspetto (es 10 vuol dire che ho mandato correttamente i primi 9 quindi mi asoetto il 10)
- TCP header length variabile: quante parole da 32 bit sono contenute nell'header
- Flag:
	- URG: urgent
	- ACK: 1 SE il campo ACK number deve essere controllato
	- PSH: push 1 SE non bisogna aspettare che il buff sia piena per mandare i messaggi
	- RST: reset: abort
	- SYN: sync usato in fase di creazione della connessione
	- FIN fine usato in fase di chiusura della connessione
- Window size: quanto al massimo puo trasmettere, cio dipende dal buffer ricevente della socket
- Checksum per verificare se il segmento è corretto
- Urgent pointer 16bit: usato un tempo per mandare CTRL C prima del comando che voglio annullare, è l offset dei dati dove iniziano i dati urgent

All'inizio della connessione i due host contrattano il MSS Max Segment Size. SE non viene definito esplicitamente, è di 536byte perche si evita una frammentazione

Il checksum non viene calcolato solo sul TCP ma sullo pseudo header: sul source IP, sul destination IP (dal DNS), protocol selector (6 per il TCP), la lunghezza del segmento + TCP header, opzioni dati ed eventualmente un padding


Come aprire una connessione (dal punto di vista di TCP non della socket)
dobbiamo decidere un sequence number 
Non posso sempre partire da 0 per evitare che pacchetti di una vecchia connessione ancora in giro causino sovrapposizione

Anche nella destinazione ci sara un contatore interno per il SEQ number

1. La sorgente invia una richiesta di connessione, un segmento in cui SYN=1 comunicando la nostra SEQ(X) (ACK non verra guardato perche il flag è a 0). Il sorgente è in stato di SYN SEN (Sent)
2. Il ricevitore controlla il checksum e risponde con un segmento in cui SYN=1 e ACK=1 comunicando il proprio SEQ(Y) e ACK che sara X+1. Il ricevente è in stato di SYN RECV (Received)
3. Il ricevitore è ora in stato di connessione established. MA il ricevente non sa se la sorgente ha ricevuto il segmento precendete, quindi viene inviato un segmento al ricevente con ACK=1 e ACK=Y+1
4. Ora entrambi hanno una connessione bidirezione indipendente (indipendente perche ci sono due SEQ indipendenti)

Oggi non viene piu usato un approccio incrementale ma viene usata una funzione crittografica

Problemi possibili:
- Non c è una porta in ascolto nella socket ricevente. Viene mandato quindi un segmento con RST=1
- ACK da ricevente a mittente non arriva in tempo. Nel mittente qiando viene inviato il suo SEQ, viene settato un RTO Round Time Trip (cioe un timer). MA inviando nuovamente la SEQ con un altra X, la prima in realta era arrivata al ricevente e riesce ad arrivare al mittente che la interpreta come errata e quindi abortisce la connessione al ricevente con un RST=1.


Come inviare dati da sorgente a destinazione (non è un flusso bidirezionale)
Assumiamo che non ci siano errori nella connessione e che la dimensione dei messaggi al livello applicazione sia maggiore della dimensione del segmento

Sorgente con messaggio da scrivere di 600byte
Sorgente con SEQ = X e destinazione con SEQ = Y
MSS = 500byte

L'applicazione del sorgente scrive il messaggio nel buffer della socket
E' necessario fare due segmenti: uno da 500 e uno da 100

1. Mando il primo segmento con SEQ = X, che conservo nel buffer TCP del mittente con tutti gli altri segmenti
2. Il ricevente controlla che sia il SEQ che si aspettava e lo mette nel buffer ricezione del TCP. Coi suoi tempi i segmenti vengono inviati dal buffer TCP a quello del receiver
3. Il ricevente manda un segmento con ACK=1, ACK = X + 500
4. Il mittente, ricevuto il segmento di ACK, cancello nel buffer TCP il primo segmento e mando il secondo segmento con SEQ=X+500
5. Ricevente ripete passo 2 mandando un ACK=X+600
6. Alla ricezione dell ACK, tutti i segmenti sono stati inviati

Per ottimizzare la trasmissione possono essere inviati piu segmenti e lato ricezione, non viene inviato subito ACK in modo che quando mi arrivi il secondo segmento (quindi in ordine), il ricevente manda un singolo ACK con SEQ dato dalla somma dei due (Cumulative ACK)

NON sempre il cumulative ACK è possibile 


Come mandare dati continuamente (es Secure Shell)
in questi casi hanno nel segmento PSH=1
Lato ricevente, una volta ricevuto il dato, oltre il segmento con ACK, viene mandato un altro segmento al mittente con PSH=1 con lo stesso dato che ha ricevuto

MA è inefficiente

Delay ACK, SE il ricevente ha qualcosa da inviare, mando sia il dato che l ACK del segmento precenìdente.
Quindi il segmento avra PSH=1, ACK=1, Ack=X+1, SEQ=Y, Data='d'

MA viene aggiunto cosi del delay aggiuntivo in cui si aspetta che l applicazione debba inviare qualcosa


Algoritmo di Nagle
Lato sorgente solo quando mi arriva l ACK del primo segmento mando insieme sia il nuovo segmento successivo che l'ACK del segmento precedente

Va bene se l applicazione non debba essere responsive


Manteniamo una variabile sia nel mittente che nel destinatario (Vs/Vr) con la Initial Sequence number 
Assumiamo ACK immediato, che quando arriva alla sorgente questa aggiorna il proprio Vs con X+500
Mandando un secondo messaggio, questo viene perso MA ho trasmesso un terzo messaggio che è arrivato alla destinazione.
Il SEQ è diverso da quello che si aspetta il ricevente, quindi lo conservo nel buffer di TCP SENZA passarlo al buffer dell applicazione
MA non posso rispondere con un ACK X+1000, quindi rispondo con un ACK X+500 perche è quello che mi aspetto
Lato mittente, si aspettava un X+1500, MA non glielo rinvio subito in quanto potrebbe arrivare in ritardo alla destinazione. Nel caso non arrivi pero, viene ignorato il problema e vengono inviati altri segmenti SENZA togliere pero dal buffer il 2o e 3o dal buffer perche non sono arrivati in ordine. Se altri messaggi arrivano al ricevente, verra inviato lo stesso ACK errato precedente, quindi viene ritrasmesso il segmento X+500 (Fast Retrasmitt) che stavolta arriva al ricevente
Il ricevente ha quindi nel buffer i segmenti in "ordine", mandando un ACK cumulativo. La sorgente quando riceve l ACK cumulativo, ripulisce il proprio buffer 

In questo modo lato mittente 3 ACK duplicati triggera il rinvio del primo segmento che stavo aspettando
Questo sistema funziona finche ho qualcosa da trasmettere, difatti non verra mai mandato un ACK al mittente. Per risolvere cio viene introdotto un timer RTO per ogni trasmissione.
Se entro RTO ricevo un altri 3 ACK, allora triggero prima della scadenza del RTO (per questo è un Fast Retrasmission) 

---

TCP è orientato allo stream di byte continuo 


Calibrazione RTO Retrasmission Time Out 
Quando si apre una connessione, non abbiamo informazioni sulla rete, quindi ci si basa sullo standard RFC 2988
Avere una buona stima del tempo medio in cui mi arriva l ACK e come outliner il caso in cui l ACK si perda
Utilizziamo una distribuzione normale con media e deviazione standard
Considero l RTO come un outliner: $\mu + k*\sigma$

- $T_0$ Momento in cui la connessione viene aperta: non ho informazioni sul RTT (Round Trip Time: da quando mando il segmento a quando ricevo l ACK). Imposto RTO a 3 secondi. Mantengono due variabili: SRTT = Null (Smoothing RTT$stima \mu$) e RTTVAR = NULL (RTT Variance stima $\sigma$) e poi G <= 100ms (G è la granularita del clock)
- Momento in cui $T_0$ scade, raddoppio l RTO (Exponential Backoff) in quanto non ho informazioni
- $T_1$ Momento in cui ricevo un segmento di ACK con un round trip time di R, imposto SRTT = R e RTTVAR = R/2. $RTO = R + max(G, k*RTTVAR)$, con k = 4 (suggerito)
es R = 10 ms, $RTO = 10ms + 4*5ms = 30ms$, quindi da 3 secondi siamo passati a 30ms
Non possiamo sempre usare questa formula 
- $T_k, k>2$, quando arriva un round trip time R, imposto $RTTVAR = (1-\beta)*RTTVAR + \beta*|SRTT-R|, con 0<\beta<1$, piu $\beta$ è vicino a 0 piu tenderò ad aggiornare meno il mio valore (Standard $\beta=1/4$)
	- Piu $\beta$ è alto, piu sono sensibile agli sbalzi di R MA se è solo un rumore temporaneo rischio di cambiare troppo
	- Piu \beta è basso, piu RTTVAR è smussato MA non cattura una variazione
  $SRTT = (1-\alpha)*SRTT + \alpha*R, con 0<\alpha<1$, (Standard $\alpha=1/8$)
  Aggiornamento $RTO = SRTT + max(G, k*RTTVAR)$ con k = 4
  SE RTO scade, raddoppio e poi quando ricevero R faro di nuovo la stima

Problemi:
- Quando l RTO scade, viene raddoppiato E viene ritrasmesso il segmento. MA se l ACK del segmento precedente arriva molto dopo, ho un ambiguita perche non si capisce a quale trasmissione del segmento appartiene. L'algoritmo di Karn dice che ogni volta che raddoppio RTO non considero RTT di nessuno dei due segmenti, non aggiornando quindi ne la media ne la varianza.


Controllo di flusso
Quanti segmenti possiamo mandare alla destinazione e la velocita di processamento alla destinazione
Lavoriamo a livello dei buffer delle socket (ricordiamo a livello kernel)

Introduciamo 2 variabili: W_S (Finestra di invio) e W_R (Finestra di ricezione) che utilizzeremo nell header del TCP in window size
Lato ricezione, notifica che la W_R = 2000, cioe ho un buffer di 2000byte (Window adv...) con un segmento con window size = 2000
Essendo a livello di trasporto, non sapro quando l applicazione leggera dal buffer (in generale utilizzera le primitive)
Quando la destinazione invia il secondo messaggio nello start della connessione, viene inclusa anche la window size, cioe la $W_R$

Ipotizziamo di avere nella sorgente un W_S= 2000
Dopo l invio di un messaggio da 500, diminuisco W_S di 500 a 1500
Invio un secondo messaggio quindi W_S=1000, e un terzo messaggio W_S=500 e un quarto arrivando con un W_S = 0.
La sorgente blocca l invio dei segmenti che avrebbe ancora da spedire aspettando che il buffer lato ricezione si svuoti

Lato destinazione, i segmenti vengono conservati nei buffer di TCP (e poi inviati al buffer dell applicazione) e l ACK (ipotizzando sia cumulativo) viene mandato alla ricezione dell ultimo segmento CON window size a 0 perche il buffer dell applicazione è pieno 

Dopo del tempo, l applicazione legge 1000 byte, quindi nel buffer dell applicazione vengono tolti 2 segmenti. Il ricevente manda quindi un segmento di ACK (con l ACK dell ultimo segmento) e con WIN=1000

Problema: l unico modo in cui riavvio l invio di segmenti è con l ACK con WIN = ...
SE tale segmento viene perso, e non c è una soluzione, si va in deadlock

La soluzione è utilizzare un Persist Timer al cui scadere il mittente mando un segmento con 1 byte di data. SE perdo tale segmento, potro inviarlo nuovamente allo scadere del Timer.
Alla ricezione, viene riconosciuto come messaggio Window Probe e viene inviato nuovamente l ACK con WIN = ... e ACK = X + 2001 


Silly Window Syndrome
Lato ricevente, ipotizziamo che l applicazione legga un byte alla volta.
MA ogni volta che si libera la finestra dovrei inviare un ACK solo per notificare una finestra di 1 byte e la sorgente invierebbe un segmento solo per un byte (con un header da ... byte)

Soluzione: algoritmo di Clark
Evitare di annunciare la nuova disponibilita di window aspettando o di raggiungere il MSS o se ho almeno meta buffer vuoto


Controllo di congestione
La congestione è un fattore della rete: è determinata dal riempimento delle code nei router e causa la perdita di segmenti
TCP vede la congestione come un errore di trasmissione
thougthput: utilizzamento del canale nel tempo
goodput: thougthput - ritrasmissioni

l obiettivo del TCP quando viene utilizzato per l invio di grandi quantita di dati, è mandare in parallelo piu segmenti possibili

Ipotizziamo di avere la trasmissione di segmenti verso una destinazione in cui in un primo tratto, ho una trasmissione veloce MA poi dal router alla destinazione ho un canale lento (collo di bottiglia). 
SE la rete ce la fa, si nota solo un aumento di RTT
SE i buffer del router si saturano, elimina i segmenti e TCP rileva l errore di trasmissione MA la sorgente come stima quanti segmenti inviare nell unita di tempo?

Finestra di congestione: quanti byte si possono immettere nella rete 
La sorgente sa che se inviato un segmento, ne ricevo l ACK, so che il segmento ha lasciato la rete 
L'unica cosa sicura è l'ACK arrivano con il tempo piu lento della rete, essendo di piccole dimensioni

Variabile $W_C$ (Finestra di congestione) viene aggiunta solo nella sorgente
Caso rete senza congestion
- Ogni volta che ricevo un ACK aumento di uno la $W_C$, risultando in un aumento veloce della finestra (in realta Slow Start con Slow come cauto) fino ad una soglia, slow start threshold
- Ora aumento W_C ogni numero della threshold ACK
- Continuo ad aumentare W_C fino a raggiungere una fase di crociera in cui non lo aumento piu 

$NumeroDiByteChePossoTrasmettere = min(W_C, W_S)$

---

Problemi:
- RTO scade, NON riceve gli ACK: congestione molto grave in quanto lo scadere del RTO è calcolato come un evento raro
Quando scade l RTO, si riparte con W_C = 1 quindi con uno slow start MA la SlowStartThreshold viene diminuita (in particolare alla meta della finistra in cui è scaduta l RTO)

- Riceve 3 ACK duplicati: alla destinazione cio che mando arriva MA arriva fuori ordine. C'è una congestione ma non è una situazione grave
con $W_C = k$ appena ricevo 3 ACK duplicati, dimezzo la finestra e riprendo ad aumentare la finestra in modo lineare

3 ACK potrebbero essere molti
La sorgente una volta capito di aver ricevuto le cose non in ordine, puo utilizzare un SACK (SelectiveACK) per specificare il segmento che ho ricevuto insieme al ACK che rappresenta invece quello che mi aspettavo


Explicit Congestion Notification
SE sappiamo che i buffer si stanno riempendo e si sta per causare una congestione, i router protrebberlo notificarlo in modo da far diminuire le finestre 

A livello IP, ci sono 2 bit che se settati a 11, vuol dire che è stato sperimentata una congestione (i router devono pero essere abilitati a gestire ECN)
Poi verra gestita dai router che non cambieranno questa informazione in modo che arriva alle destinazioni
Il router marca quindi ECE (ECN Echo) a 1 in modo che tutti gli ACK che manda lo avranno in modo da notificare il router

Le primitive IP informano il TCP riducendo cosi la finestra nelle destinazioni
Il bit CWR (CongestionWindowReduced) viene quindi settato a 1 nei successivi segmenti in modo che la destinazione informi i router di aver ridotto la finestra



Come chiudiamo la connessione 
(Chiusura simultanea da saltare)
- Chiusura normale (4 vie/4 way close): client ha ricevuto tutti gli ACK e il sever non ha niente da fare in sospeso
Abbiamo un TCP Client e un TCP Server
Abbiamo inizialmente EST, EST (EST = Established) da entrambi i lati

L'applicazione chiama la primitiva close()
Viene mandato il segmento al server con FIN=1 e SEQ = X
Il client entra in stato di FIN_WAIT1 mentre il server quando riceve il segmento (in particolare l'applicazione receive(EOF)), entra in stato CLOSE_WAIT
Il server manda un segmento con ACK, ACK=X+1 (facendo entrare il client in FIN_WAIT2) e dopo un certo tempo l'applicazione del server chiama la close(), mandando un segmento con FIN e SEQ=Y
Quando lo riceve il client entra in TIMEDWAIT in un loop e manda un segmento ACK, ACK = Y
Il server ricevendo l ACK, fa la close  
Lato client dopo 2MSL (Max Segment Lifetime) la socket viene chiusa

- Chiusura a 3 vie: il client chiede la chiusura nonostante non abbia ricevuto tutti gli ACK
MA nel server ho ancora dei segmenti di cui devo mandare l ACK
L'applicazione del server, ricevendo EOF, fa la close()

MA dato che devo mandare al client un ACK, mando FIN, ACK, ACK=X+N (con N ACK mancanti)
Client mandera ACK, ACK = Y+1

Sia chiusura a 3 che a 4 vie NON ho dati (NON ACK) da inviare

- Chiusura Half-Close: client ha finito di inviare dati MA server deve ancora inviare dati al client
Si usa la primitiva shoutdown() per notificare che si è finito di inviare dati
Anche in questo caso AP del server riceve EOF MA il server non ha finito di inviare, cosi continua con le proprie send(NByte) mandandoli insieme a ACK, ACK = X+1, SEQ = Y, NByte. 
Lato server, avra ora X, EST e lato client avra X, EST
Il canale Server-Client è ancora attivo, riuscendo quindi a mandare l ACK al server per il segmento ricevuto
Si ripete finche l AP del server chiama shoutdown() chiudendo la parte di stream rimanente, mandando un segmento con FIN, SEQ=Y+N
In risposta il client mandera ACK, ACK=Y+N+1


SE il client muore prima di mandare l ACK di chiusura, il server aspetta 2 ore e poi inizia a inviare per 10 volte un KA prob con seq = X-1 ogni 75secondi, SE non risponde, il server chiude la connessione


TCP option
Le opzioni sono multipli interi di 32 bit nell header TCP
Max Segment Size Option
- Campo che identifica l opzione es Kind=2 -> Max Segment Size Option
- Campo che identifica la lunghezza in byte es lenght = 4 
- Option


Inefficienza SE banda/RTT alta, posso mandare molti dati, molti piu dei 16 byte della window size
Window scale option: kind = 1, Kind = 3, Length = 3, Shift count
Kind = 1 è una NOT Option per fare padding e raggiungere i 32 byte
Lo shift count = 0 SE non viene fatto uno scaling
è = 1 SE multiplico per 2^1
...


Time stamp option: deve essere abilitata durante l apertura della connessione
Kind = 1, Kind = 1, Kind = 8, Length = 10
Time stamp value (quando è stato inviato il segmento dalla sorgente)
Time stamp echo reply 

Serve nei casi in cui la finestra sia abbastanza grande e quindi la stima dell RTT deve essere precisa
SE pensiamo ad una sorgente che manda quasi instantaneamente N messaggi ma questi non arrivano insieme alla destinazione ma dilatati. SE mando un ACK cumulativo sto in realta sovrastimando a causa dell ultimo segmento

Con i timestamp invece, quando ricevo il primo segmento dopo un ACK, salvo il timestamp in TSRecent e cosi nell ACK cumulativo usero TSE = TSRecent. 
Nella sorgente al tempo t3 stima RTT = t3-FirstTS (e quindi non t3-t2)


Riassunto RCP
Controllo dell errore
Controllo del flusso
Controllo di congestion

Timer:
RTO 
Persistent Time 
KeepAlive Timer
TimeAwaitFin

Option
SACK
WindowScale
TimeStamp



UTP UserTProtocol
in TCP si perde la divisione dei messaggi perche è tutto uno stream
Unico controllo in UTP è il checksum

UTP è orientato al messaggio (al massimo 64kByte) (NON uno stream di byte)
Stesse cose che garantisce IP ma al livello 4

es DNS e protocolli real time usano UTP 
Vantaggi: non c è apertura della connessione (usato proprio quando non si vuole la parte di connessione), non c è la finestra di congestione


Protocollo QUIC Quick UDP Internet Connections
Voglio usare il protocollo HTTP, sia HTTP 1.1 che 2 usano TCP
- Quando cambio rete, cambia indirizzo IP e quindi la connessione TCP viene rotta, chiusa e riaperta con il nuovo IP. Ho quindi nuovamente uno slow start percepibile
- SE si vogliono fare piu richieste TCP per parallelizzare, devo aprire N connessioni che possono appesantire il server
- Anche se utilizzassi una connessione, TCP non distingue i tipi di richieste (testo, immagini) quindi se nel buffer ho molti segmenti MA ne manca una parte di una richiesta (perche non distinguendo i messaggi ha diviso lo stream male), resteranno bloccati senza arrivare all applicazione. (es devo mandare M1 e M2 MA vengono divisi in 3 segmenti con il secondo che ha un parte di M1 e una di M2, che quando viene perso blocca anche gli altri due anche se sono arrivati) 

QUIC a livello di trasporto permette di avere piu stream concorrenti e indipendenti, ognuno con un controllo di flusso, ... tutte in un unica connessione QUIC
Visto che UDP non garantisce nulla, QUIC fa tutti i controlli che fa TCP
Mentre TCP e UDP lavoro a livello Kernel, QUIC lavora a livello User 


