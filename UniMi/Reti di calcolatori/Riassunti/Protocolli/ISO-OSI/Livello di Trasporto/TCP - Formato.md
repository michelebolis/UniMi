header: (foto del libro antiquata)
- porta sorgente 16bit: scelta dall Host (solitamente >1000 perche sono per lo user)
- porta destinazione 16bit: porta nota 
- Sequence number 32 bit: indica l inizio dei byte che vengono trasmessi in un segmento TCP
- ACK number 32 bit: identifica il byte successivo che mi aspetto (es 10 vuol dire che ho mandato correttamente i primi 9 quindi mi asoetto il 10)
- TCP header length variabile: quante parole da 32 bit sono contenute nell'header
- Flag:
	- URG: urgent
	- ACK: 1 SE il campo ACK number deve essere controllato
	- PSH: push 1 SE non bisogna aspettare che il buff sia piena per mandare i messaggi
	- RST: reset: abort
	- SYN: sync usato in fase di creazione della connessione
	- FIN fine usato in fase di chiusura della connessione
- Window size: quanto al massimo puo trasmettere, cio dipende dal buffer ricevente della socket
- Checksum per verificare se il segmento è corretto
- Urgent pointer 16bit: usato un tempo per mandare CTRL C prima del comando che voglio annullare, è l offset dei dati dove iniziano i dati urgent

All'inizio della connessione i due host contrattano il MSS Max Segment Size. SE non viene definito esplicitamente, è di 536byte perche si evita una frammentazione

Il checksum non viene calcolato solo sul TCP ma sullo pseudo header: sul source IP, sul destination IP (dal DNS), protocol selector (6 per il TCP), la lunghezza del segmento + TCP header, opzioni dati ed eventualmente un padding

[[TCP - Option]]

Formato record:
- Numero variabile di parole a 32 bit di FullyQualifiedDomainName
- 16 bit di type in quanto ci sono diverse tipologie di record
	- SOA Start of authority: da i parametri della zona che sya gestendo il server
	- A: IPv4
	- AAAA: IPv6
	- MX: Mail Exchange
	- NS: Name server restituisce l IP del server DNS
	- CNAME: alias del server
	- Pointer: per la mappatura da indirizzo IP a nome
- 16 bit di class, sempre = 1 cioè Internet
- 32 bit di TTL in secondi di memorizzazione del record in cache
- 16 bit length
- record data cioè l'indirizzo richiesto

Formato query
- 32 bit query header
- 32 bit query domain name
- 16 bit query type -> record type 
- 16 bit query class
DNS response message: alla query vengono aggiunti 32 bit di Resource record