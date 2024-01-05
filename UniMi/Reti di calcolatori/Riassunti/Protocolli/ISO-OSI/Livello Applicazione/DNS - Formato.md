Formato record:

| Campo                      | Dimensione | Descrizione                              |
| -------------------------- | ---------- | ---------------------------------------- |
| N FullyQualifiedDomainName | $N*32bit$  | deve essere meno di 256 caratteri con l ultimo byte a 0 (la root)                                         |
| Type                       | 16 bit     | ci sono diverse tipologie di record      |
| Class                      | 16 bit     | = 1 cioè indica l'utilizzo di Internet                        |
| TTL                        | 32 bit     | secondi di validità della memorizzazione |
| Length                     | 16 bit     |                                          |
| Data                           |            | l'indirizzo richiesto                                         |

| Tipo di record         | Descrizione                                          |
| ---------------------- | ---------------------------------------------------- |
| SOA Start Of Authority | da i parametri della zona che sta gestendo il server |
| A                      | IPv4                                                 |
| AAAA                   | IPv6                                                 |
| MX                     | Mail Exchange                                        |
| NS Name Server         | restituisce l'IP del server DNS                      |
| Pointer                       | per la mappatura da indirizzo IP a nome                                                     |

Formato DNS query message

| Campo                    | Dimensione |
| ------------------------ | ---------- |
| Query header             | 32 bit     |
| Query domain name        | 32 bit     |
| Query type = Record Type | 16 bit     |
| Query Class                         | 16 bit           |

DNS response message: alla query vengono aggiunti 32 bit di Resource Record