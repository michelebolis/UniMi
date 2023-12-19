Dato che IP è un servizio best-efford, i pacchetti potrebbero essere scartati mentre sono in transito.
SE un pacchetto è scartato per qualsiasi motivo tranne la corruzione di informazioni, ICMP Internet Control Message Protocol nell'host che scarta il pacchetto, genera un messaggio di errore che viene mandato al mittente, in particolare all'ICMP del mittente.

SE un'amministratore di rete riceve come messaggio che una destinazione non risponde, la causa puo essere determinata utilizzando la funzione di reachability testing implementata con il ping. Viene inviata una echo request che una volta ricevuta dall'ICMP, ritorna una echo reply

Si occupa della rilevazione degli errori, verifica la raggiungibilità (server utilizzano ICMP per verificare che l'IP che si vuole assegnare non sia gia utilizzato), controllo di congestione (trasmette check packet che segnalano verso i nodi vicini, la situazione congestionata del nodo in modo che venga evitato quel nodo), misura prestazioni...

| Message type            | descrizione |
| ----------------------- | ----------- |
| Destination unreachable |             |
| Echo request            |             |
| Echo reply              |             |
| Timestamp request       |             |
| Timestamp reply         |             |
| ...                        |             |

![[Pasted image 20231219091724.png| 300]]
