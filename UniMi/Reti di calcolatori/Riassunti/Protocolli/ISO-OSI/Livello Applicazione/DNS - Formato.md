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