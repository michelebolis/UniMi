In TCP si perde la divisione dei messaggi perche è tutto uno stream
UTP è orientato al messaggio (al massimo 64kByte) (NON uno stream di byte)
La trasmissione viene demandata al layer IP su Internet

Formato

| Campo | Dimensione | Descrizione |
| ---- | ---- | ---- |
| source/destination port | 16 bit | numero di porta del protocollo applicazione  |
| length |  | numero di byte header (8 byte) + dati |
| checksum |  | unico controllo in UTP  |
| dati |  |  |

es DNS e protocolli real time usano UTP 
Vantaggi: non c'è apertura della connessione (usato proprio quando non si vuole la parte di connessione), non c'è la finestra di congestione