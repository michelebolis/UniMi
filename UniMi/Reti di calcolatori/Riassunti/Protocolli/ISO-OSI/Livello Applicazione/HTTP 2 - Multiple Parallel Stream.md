HTTP 2 crea, `sulla stessa connessione TCP, piu stream paralleli indipendenti`. 
Per farlo si introducono gli `stream`, canali eventualmente bidirezionali, a livello applicazione (quali stream far passare, quale stream leggere...) mentre a livello TCP abbiamo un demultiplexing. 

Vantaggio di avere piu stream: `posso cambiare priorita di invio in base allo stream` e `non dover aspettare che venga inviato tutto di uno stream prima di inviare un altro stream`. 
Unico vincolo: all interno dello stream l `ordinamento è FIFO`

Ciclo di vita dello stream
- `Idle`: non è allocato ne sul server ne sul client
- `Open`: SE faccio SEND Header oppure RECEIVE Header. Rimane aperto fin quando non ricevo o mando un qualunque frame con flag RESET
- `Closed`

A seconda che io riceva o mandi una PUSH PROMISE cambiano gli scenari
- `Reserved local`: quando faccio SEND PUSH PROMISE
	- `Half Closed Remote`: quando faccio SEND HEADER. Significa che questo stream è utilizzato SOLO da chi l ha creato per inviare (stream unidirezionale)
- `Reserved remote`: quando recevo RECEIVE PUSH PROMISE