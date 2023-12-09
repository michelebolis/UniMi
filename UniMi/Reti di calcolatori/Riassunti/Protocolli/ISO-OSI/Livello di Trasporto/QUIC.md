Protocollo QUIC Quick UDP Internet Connections
Voglio usare il protocollo HTTP, sia HTTP 1.1 che 2 usano TCP
- Quando cambio rete, cambia indirizzo IP e quindi la connessione TCP viene rotta, chiusa e riaperta con il nuovo IP. Ho quindi nuovamente uno slow start percepibile
- SE si vogliono fare piu richieste TCP per parallelizzare, devo aprire N connessioni che possono appesantire il server
- Anche se utilizzassi una connessione, TCP non distingue i tipi di richieste (testo, immagini) quindi se nel buffer ho molti segmenti MA ne manca una parte di una richiesta (perche non distinguendo i messaggi ha diviso lo stream male), resteranno bloccati senza arrivare all applicazione. (es devo mandare M1 e M2 MA vengono divisi in 3 segmenti con il secondo che ha un parte di M1 e una di M2, che quando viene perso blocca anche gli altri due anche se sono arrivati) 

QUIC a livello di trasporto permette di avere piu stream concorrenti e indipendenti, ognuno con un controllo di flusso, ... tutte in un unica connessione QUIC
Visto che UDP non garantisce nulla, QUIC fa tutti i controlli che fa TCP
Mentre TCP e UDP lavoro a livello Kernel, QUIC lavora a livello User 
