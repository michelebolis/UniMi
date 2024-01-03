Protocollo RIP: implementazione del DV
RIP usa una policy `triggered update`: ogni nodo quando rileva una destinazione tra le adiacenti non raggiungibili mettendo nella propria tabella la entry a infinito. INVECE di aspettare la scadenza di timer per la ritrasmissione del DV, il DV viene mandato immediatamente 

Come metrica RIP utilizza SOLO hop count
L'infinito è considerato $n>16$: non si utilizza quindi RIP per reti con diametro maggiore di 16
Usa un random per il trigger, tutte le volte che rilevo un costo infinito non faccio un update instantaneo ma aspetto un tempo casuale per evitare storm the ...