`NAT-  Network Address Traslation `
`Per ogni rete di accesso, viene assegnato un solo indirizzo IP` in questo modo separo internet con il NAT da un insieme che è in grado di concentrare un numero elevato di macchine

Gli Host non utilizzano un indirizzo IP pubblico MA un indirizzo IP privato
L'indirizzo pubblico è unico al mondo mentre quello privato è assegnato dall'amministratore della rete locale
Quando un Host della rete deve comunicare attraverso Internet, dovrà utilizzare un indirizzo pubblico trasformando il proprio indirizzo privato a pubblico attraverso il NAT

All'interno dell'header TCP vi è il `numero della porta dell'origine` che identifica l'applicazione che ha fatto la richiesta e il `numero di porta della destinazione` che identifica la corrispondente applicazione del computer remoto
Associato al router NAT, vi è una `NAT table` che contiene per ogni sessione due entry.
- Lato richiedente, l'entry comprende l'IP privato dell'interfaccia dell'host e il numero di porta d'origine allocato
- Lato ISP, l'entry è composta dall'IP e da un numero di porta assegnato dal NAT router
In questo modo si evita che si utilizza la stessa porta TCP in diversi host

`Da standard quindi il livello 3 guarda l'header del livello 4`
`Porta destinazione 80 = Internet`

MA se due macchine usano la stessa porta sorgente non funziona. 
Il NAT crea quindi un altra entry in cui è il NAT che da il numero di porta sorgente, evitando quindi sovrapposizioni

Problema: Access Gateway non conosce il MAC address della macchina destinataria, o in generale su una rete che instrada con un indirizzamento diverso: [[ARP-RARP]]

[[NAT - Esempio]]