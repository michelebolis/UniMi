Reti punto punto : topologia magliata in cui i nodi sono collegati 
OSS abbiamo un unico processo di livello 3 MA tanti processi di livello 2 quante sono le porte I/O


Timer inizializzato quando viene mandato F e resettato all'arrivo dell'ACK

per tutto il tempo $T_x$ il driver sicuramente è occupato


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