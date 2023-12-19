| Campo                          | Dimensione   | Descrizione                                                                                                                                                                                    |
| ------------------------------ | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Version                        | 4 bit        | specifica se sia un IPv4 o IPv6                                                                                                                                                                |
| IHL Intermediate Header Length | 4 bit        | specifica la lunghezza dell'header come multiplo di 32 bit. La lunghezza minima senza opzioni è di 5, mentre il massimo permesso è 15.                                                         |
| TOS Type Of Service            | 8 bit        | specifica la priorita dell'applicativo e gli attributi relativi al path da seguire                                                                                                             |
| Total lenght                   | 16 bit       | definisce la lunghezza totale del pacchetto (header+payload). La lunghezza massima del pacchetto è di 64k-1 bytes. Questo campo sarà utilizzato dalla destinazione per riassemblare il payload |
| Identification                 | 16 bit       | utilizzato nella frammentazione                                                                                                                                                                |
| Flag bits                      | 3 bit di cui |                                                                                                                                                                                                |
| D bit                          |              | indica se il pacchetto è stato frammentato o meno                                                                                                                                              |
| M bit                          |              | More fragment indica SE se ci sono altri frammenti del pacchetto (sarà 0 sull'ultimo frammento)                                                                                                |
| Fragment Offset                | 13 bit       | indica l'offset, in multipli di 8 bytes, rispetto all inizio del pacchetto                                                                                                                     |
| TTL Time To Live               | 8 bit        | definisce il tempo massimo per il pacchetto in transito, verra decrementato in ogni gateway/router. E' usato per rilevare eventuali loop                                                       |
| Protocol                       | 8 bit        | usato per permettere alla destinazione IP di passare il all'interno di ogni pacchetto ricevuto allo stesso protocollo che ha mandato i dati (es ICMP or TCP or UDP)                            |
| Header checksum                | 16 bit       | per rilevare errori                                                                                                                                                                            |
| Source/Destination             | 32 bit       |                                                                                                                                                                                                |
| Option                         | 0-40 bytes   | può contenere per esempio il path da seguire per raggiungere la destinazione                                                                                                                   |
| Payload                        |              |                                                                                                                                                                                                |

![[Pasted image 20231219091112.png]]

[[NetID]]

