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
attaccata alla porta di rete abbiamo il bus di comunicazione con la coda di uscita Tx, con delle word di una certa dimensione.
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
HA passa entra in uno stato di Wait una volta che ha mandato i bit da Tx; durante questo tempo il canale non è utilizzato.
Il problema è che l'ACK potrebbe non arrivare, in quanto potrebbe essere perso o corrotto


Il Jitter è definito dalla deviazione standard, importante per alcuni applicativi che necessitano stabilità di comunicazione (es videogiochi)
La media è comunque importante 

In realta per la maggior parte dei casi non è richiesta affidabilita ma piuttosto la velocita (es voce in videochiamata, caso contrario una mail)


La rete fornisce gli strumenti per essere configurata dalle varie applicazioni, quindi deve essere abbastanza flessibile da potersi adattare alle richieste degli applicativi.

Un protocollo è un insieme di regole e convenzioni che permettono la comunicazione due entità. Ovviamente le due entità devono usare lo stesso protocollo.


Consideriamo A e B collegati da un solo cavo
- Tempo di trasmissione Tx = datiDaTrasmettere/capacitaCanale 
	- dipende dalla capacita del canale e dalla velocità di immissione del mittente.
- Tempo di propagazione Tp: distanza / velocità
	- è il tempo che un pacchetto impiega da A a B
	- dipende unicamente dalle caratteristiche fisiche del canale su cui viaggiano i dati (lunghezza e materiale fisico)
- Tp+Tx tempo che intercorre da quando il primo bit esce a quando l ultimo bit arriva
	- Tp aumenta molto fino a superare Tx quando le distanze aumentano (comunicazioni satellitari, continentali)

Anche l'ACK è un pacchetto, che viaggia nella direzione opposta quindi dobbiamo considerare anche TxACK e il TpACK
OSS Tp e TpACK sono uguali, perche è lo stesso canale e la stessa distanza 
TxACK vogliamo che si minimizzi: per far cio minimizziamo il peso dell'ACK, tanto da risultare spesso irrilevante nella stima del tempo.

Per riconoscere che non sia arrivato un ACK, faccio trascorrere un tempo minimo calcolato come: Tx + 2 Tp

Una volta inviato un pacchetto, ne tengo una copia nel buffer del Kernel finchè non mi ricevo ACK. Stessa cosa anche il ricevente, tiene una copia del pacchetto nel buffer del Kernel finchè non riceve tutti i pacchetti del file.
Una volta inviato un pacchetto, parte un timer per il Waiting che stima il tempo minimo, cioè Tx + 2 Tp sovrastimato

SE ACK non arriva A non sa se è arrivato il pacchetto, quindi lo manda nuovamente. 
L'Host ricevente riconosce se il pacchetto fosse gia arrivato nei buff. Nel caso ce l'abbia già lo scarta, mandando lo stesso l'ACK al mittente.


SE la rete è affidabile e succedono degli errori, siamo in grado di risolverli dagli host (non dalla rete)

---

In Tp consideriamo il tempo del singolo bit perche la capienza del messaggio totale è utilizzata nel calcolo di TxP1

In un caso piu generale oltre al tempo di propagazione del canale in se abbiamo piu router coinvolti, ognuna con le proprie code che causano un tempo di coda Tq.
Il tempo complessivo è piu complicato da stimare

Tempo di invio completo: Tx+ Tp + Tq + TxR1 + ...
Tq: tempo di coda nel singolo router


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
es dopo poche interazione HB arriva ad avere il buffer pieno ed inizia a buttare via cio che gli arriva 
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


- Cavo coaxial: cavo di rame

- Cavo fibra ottica
E' formato da una parte di vetro in cui passa la luce
- Multimodale: la luce viaggia grazie alla riflessione continua della luce grazie ad un angolo critico per effetto della rifrazione
Lato mittente, c è un laser o un diodo che manda gli 1 o 0 mentre lato destinatario vi è un ricevitore ottico per leggere le informazioni


Differenze
- costo
- proprieta di attenuazione: la fibra ha attenuazione minore (attenuazione: diminuzione progressiva dell'intensità di un segnale) del doppino telefonico (doppino massimo teorico 100m)