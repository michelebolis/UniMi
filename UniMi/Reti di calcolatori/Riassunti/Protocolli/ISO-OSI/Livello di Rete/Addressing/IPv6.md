Feature
- Spazio di indirizzamento aumentato da 32 a 128 bits
- Header semplificato permette ai router di processare e instradare i pacchetti piu velocemente
- migliorata la sicurezza

Header di 40 bytes

| Campo                      | Dimensione | Descrizione                                                                                                                                                                                                           |
| -------------------------- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Version                    | 4 bit      | settato a 6                                                                                                                                                                                                           |
| Traffic                    | 8 bit      | simile a ToS. Permette al mittente IP di allocare una diversa priorita ai pacchetti                                                                                                                                   |
| Flow label                 | 20 bit     | settato a 0 SE è un pacchetto best-efford altrimenti è usato per permettere al router di identificare i pacchetti di una stessa sessione                                                                              |
| Payload length             | 16 bit     | indica il numero di bytes che seguo l'header di 40 bytes (ATT nell'IPv4 questo campo comprendeva anche l'header). MIN: 536 bytes, MAX 64kk bytes                                                                      |
| Next header                | 8 bit      | IPv6 comprende un header principale seguito da altri header tra cui quello di TCP/UDP, oppure da [[IPv6 - Extensions headers\|Extensions headers]] inseriti tra quello principale e l'header del livello di trasporto |
| Hop limit                  | 8 bit      | simile a time to leave ma stavolta vengono contati gli hop, venendo decrementato di 1 ogni volta che viene inviato                                                                                                    |
| Source/Destination address | 128 bit    | IPv6 è assegnato all'interfaccia fisica NON all'host o router                                                                                                                                                         |
| Payload                    |            | Upper bound del payload sempre di 64K                                                                                                                                                                                 |

![[Pasted image 20231219091422.png]]

[[Interazione IPv4 - IPv6]]