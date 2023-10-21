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


dal livello 3 in su è dell'host
il livello 1 e 2 riguarda invece la rete 

al livello 3 abbiamo 2 funzioni
- Addressing: indirizzo numero per indentificarsi. Consente di indirizzare dei dispositivi remoti alla rete
- Rowting / instradamento: cammino migliore per raggiungere la destinazione

Ci sono delle code di input, delle code di output
input: unita dati del livello 3: pacchetti
Processo di forwarding: metta input in output in base a una tabella in cui per ogni destinazione esiste una linea di output. Tabella popolata non solo con le destinazioni della rete ma con tutte quelle di Internet
Questo è possibile grazie al processo di rowting che raccoglie dati, li processa, e popola le tabelle di rowting. E' necessario che abbia conoscenza della topologia di rete grazie alla quale popola la tabella 


