NAT Network Address Traslation 
Dispositivo (router) che si occupa di tradurre indirizzi
Separo internet con il NAT da un insieme che è in grado di concentrare un numero elevato di macchine
Gli Host non utilizzano un indirizzo IP pubblico MA un indirizzo IP privato
L'indirizzo pubblico è unico al mondo mentre quello privato è assegnato dall'amministratore della rete locale
Quando un Host della rete deve comunicare attraverso Internet, dovrà utilizzare un indirizzo pubblico trasformando il proprio indirizzo privato a pubblico attraverso il NAT

10.0.0.0 - 10.255.255.255
...

Basta un indirizzo IPv4 pubblico per rappresentare centinaia di dispositivi privati

es 
host: 10.0.0.1 
NAT: 194.24.16.0
Server: 200.10.0.0

Tabella NAT

| IP sorgente | IP NAT      | IP destinazione | # Porta Sorgente | # Porta destinazione |  Porta NAT   |
| ----------- | ----------- | --------------- | ---------------- | -------------------- | --- |
| 10.0.0.1    | 194.24.16.0 | 200.10.0.0      | 10               | 80                   |10     |
| 10.0.0.4    | 194.24.16.0 | 200.10.0.0      | 15               | 80                   | 11    |

Identificatore logico ricavato dal livello 4 
TCP comunica con i processi applicativi grazie alla porta logica, un identificatore numerico univoco logico all interno della macchina
La porta logica è l'"indirizzo" del livello 4, viene salvata nell header di TCP
La porta è un descrittore di socket

Da standard quindi il livello 3 guarda l header del livello 4
Avra bisogno di avere anche una maschera del livello superiore

Porta destinazione 80 = Internet

MA se due macchine usano la stessa porta sorgente non funzione. Il NAT crea quindi un altra entry in cui è il NAT che da il numero di porta sorgente, evitando quindi sovrapposizioni

Lato destinatario: per aprire il mio sito all esterno, apro la porta di servizio 80 sull'indirizzo del server

Problema: Access Gateway non conosce il MAC address della macchina destinataria, o in generale su una rete che instrada con un indirizzamento diverso: [[ARP]]