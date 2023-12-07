in TCP si perde la divisione dei messaggi perche è tutto uno stream
Unico controllo in UTP è il checksum

UTP è orientato al messaggio (al massimo 64kByte) (NON uno stream di byte)
Stesse cose che garantisce IP ma al livello 4

es DNS e protocolli real time usano UTP 
Vantaggi: non c è apertura della connessione (usato proprio quando non si vuole la parte di connessione), non c è la finestra di congestione