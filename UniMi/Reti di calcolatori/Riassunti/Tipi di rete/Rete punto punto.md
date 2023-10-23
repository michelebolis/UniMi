Reti punto punto : topologia magliata in cui i nodi sono collegati 
OSS abbiamo un unico processo di livello 3 MA tanti processi di livello 2 quante sono le porte I/O


Tra il livello 2 al livello 1 il trasmettitore aggiunge una sequenza di bit all'inizio e alla fine, flag formata da 8 bit: 0 111 111 0
In idle il ricevitore legge tutti 1 o tutti 0, quindi quando riceve il flag il ricevitore inizia a sincronizzare il proprio clock in quanto sa che dopo lo 0 si deve aspettare 6 1 e poi lo 0.
A livello fisico dopo aver ricevuto lo 0, processo bit a bit gli 1 contandoli con un contatore, sia all'inizio che alla fine 

E' la flag di HTLC

Il ricevitore sa che la sequenza finale di flag non è il payload grazie al bit staffing che aggiunge nelle sequenze che corrispondono al flag uno 0 dopo 5 1 (il ricevitore aggiunge un delay di un bit)
Il transriver del ricevitore processa e toglie le flag all'inizio e alla fine, non arrivando quindi al 2o livello


Il protocollo per la correttezza lo mette al livello 2 quando so che il canale è molto inaffidabile 
Mettere HTLC al livello 2 costa molto in termini di tempo
Ora il tasso di errore del canale è diminuito, lasciando che se ne occupi il livello 4
Oggi usiamo un livello 2 affidabile sul canale radio e wireless 



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


Campo sequence: numero di sequenza
Fisicamente è presente nell'header (in bit) MA quanto può essere grande una finestra a livello 2?
in HTLC ci sono 4 bit di seq