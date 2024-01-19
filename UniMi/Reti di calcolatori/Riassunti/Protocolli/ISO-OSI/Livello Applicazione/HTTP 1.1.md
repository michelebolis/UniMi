SE devo trasferire tanti dati su una connessione TCP, inizialmente ho uno slow start MA se dopo pochi secondi faccio un altra richiesta, si apre una nuova connessione ricominciando con lo slow start
Con l `opzione KeepAlive` possiamo mantenere aperta la connessione per un certo tempo
Dalla fine dell'inizio della connessione, uso la stessa connessione, anche se inutilizzata, finche non chiudo la pagina o non finisce il KeepAlive

SE so che devo inviare N richieste, è inutile che ne invii una alla volta aspettandone la risposta
`Request pipeline`: invio tutte le richieste e aspetto tutte le risposte
Limite: `l'ordine con cui restituisco le risposte deve essere lo stesso con cui ho ricevuto le richieste` (a livello di protocollo il client non riesco a riconoscere le richieste che ha fatto)
Svantaggi: l'ordinamento cosi definito non ottimizza le risposte in quanto SE invio A e B, e A è piu pesante di B, A "rallenta" B (complica la gestione delle risorse)

Per ottimizzare il client apro piu connessioni parallelizzando appesantendo pero il server 
