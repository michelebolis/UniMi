Perché EOLO esiste? EOLO è un operatore FWA Fixed Wireless Access cioè il tratto tra cabina al cliente avviene attraverso onde radio (NON cavo)
L'Italia ha una popolazione molto distribuita in un territorio molto eterogeneo

Cablare il paese con la fibra ottica costa molto
La tecnologia EOLO ha permesso di raggiungere piccoli paesi non raggiunti da rete cablata
In realtà è anche a livello europeo 

L'Italia è sotto la media europea per connettività

2000: le soluzioni di networking erano proprietario e chiesto con forti vincoli di standard
Si cercava di far percepire una necessita e di farla standardizzare

es al tempo T0 vi è la necessita di utilizzare un nuovo protocollo
si stima un tempo necessario fino ad ottenere la necessita, di cerca 4 anni
Vi era una specie di lobbing da parte del produttore, riscontrabile anche dal numero di RFCs

2008: disaccoppiamento HW e SW
OpenFlow nuovo tipo di standard 

2012: si pensa di virtualizzare alcune parti della rete es Firewall, regole di frammentazione

2016: paper di Google SDN SW Defined Networking

nascono societa apposite come Barefoot Networking che offre switch programmabili senza passare per uno standard intermediario 


Incentivi: numero di utenti che utilizza internet è in aumento, soprattutto quello dei mobile user 
Filosofia Open Networking: assumendo che l HW è diventata una commodity (una cosa scontata), posso pensare a come programmare il SW senza pensare all intermediario protocollare

in EOLO ci sono delle torri con trasmettitori di onde radio
Si forma una rete molto magliata
Ci sono dei datacenter che ospitano tutta l infrastruttura SW, collegati ai vari POP regionali che si connettono alle torri, tra loro connesse in modo cablato o sempre attraverso onde

Backhaul PTP PointToPoint cioe collegamento tra torri
PMP PointMultiplePoint cioe collegamenti tra torre e il client

Problematiche
la fibra ottica trasporta luce quindi è immune dai cambiamenti ambientali (es temperatura) MA non è sempre disponibile, quindi le torri vengono collegati tramite frequenza che piu si aumenta, e piu è soggetta all ambiente (es ossigeno, pioggia, nebbia)
La banda non è quindi costante

Il traffico richiesto aumenta dalle 5 del mattino fino alle 22 dove inizia a diminuire, con un picco di 1490G al secondo richiesto
Inoltre con il COVID è stata raddoppiato la domanda 
es TIM ha picco di 6T

La quantita di traffico continua ad aumentare perche TCP è un protocollo di business, cioe le grandi aziende riescono a erogare servizi sempre al limite verso la congestione della rete
In realta quindi piu banda metti, e piu le grandi aziende te ne occupano

EOLO ha inventato i propri router 
model 1 per applicazione di rete in modo da parallelizzare molto la gestione del traffico grazie ai 72 core facendo polling e riuscendo a consumare poco (90W)

model 2 basato su intel con lo svantaggio di consumare di piu (210W) ma fornendo una gestione piu semplice

Problema nei test sono spesso alcune frequenze per gli alimentatori
Test anche per le temperature estreme, dai -15 ai +75 (montagna-tangenziale d estate)
Gli alimentatori ad alte temperature perdono efficienza 


Lato SW si usa un kernel linux 
OpenVSwitch permette di far diventare un router uno switch virtualizzando. Programmabile con OpenFlow
6WIND far diventare le CPU dedidate per la parte di rete, da interrupt a polling baipassando il kernel e funzionando in userspace (molto efficiente). DPDK si sincronizza col kernel in modo che se metto OpenVSwitch vengano usate
...
Quagga suit di protocollo di routing per usare di BGP

Hanno sviluppato anche un framework per la gestione di questi router : BLUE Gateway
Implementate delle fujnzionalita di esecuzione di comandi in modo parallelor, la schedulazione notturna di task, rilevamento di successo/fallimento e successivo rollback
Riesce a rilevare la topologia della rete in tempo reale, fornire statistiche su utilizzo delle CPU, stato della rete, temperatura della board
Ha anche il vantaggio di aiutare ad evitare l errore umano


Soluzione 1: pure L2
Hanno fatto una rete L2 con un approccio protocollare costruendo spanning tree per VLAN
Vengono virtualizzate alcune funzioni
Per fare bilanciamento del traffico, quando vedo link satura, modificano le porte dei router in modo che diniscano su VLAN diverse

Svantaggi: L2 convergenza molto lenta (30s) e un numero molto elevato di MAC address perdendo il traffico (esplosione quadratica delle flow con il numero di router)


Miglioramento:
In un L2 mi interessa solo la destinazione: hanno riscritto parte del codice mettendo wildcard sulla sorgente, in modo da diventare lineare con il numero del router 

Soluzione 2: approccio SDN SW Defined Networking
Tolgo tutti i protocolli e gestisco i router da un controller centralizzato
BLUGW sa la capacita dei link, la banda desiderata in real time e in base a cio calcola il cammino migliore
Il gateway istruisce quindi tutta la rete su come instradare il traffico con label MPLS

SE un link diminuisce la sua capacita, il BLUGW ricalcola il percorso

Problemi: granularita di OpenFfow è molto piccola (devo aggiornare tutta la rete per una flow modificata) e ogni volta che la capacita di rete o la rete cambia devo ricalcolare tutte le rotte (problema dello zaino). Le modifiche devono essere atomica MA c è un alto rischio di inconsistenza. Inoltre non c è un modo per tornare ad una configurazione sicura (tutto centralizzato)

Soluzione 3 (attuale): paradigma Segment routing
modello di routing che mima la spedizione delle lettere, una sorta di tunneling mettendo una destinazione intermedia per arrivare alla destinazione finale
Fault management gestito con BGP centralizzato
Ottimizzazione con segment routing 

al tempo 0 tutti i router imparano il cammino migliore in modo indipendente (soprattutto in caso di fault di un link)

Ottimizzazione
Riutilizziamo le informazioni realtime facendo un ottimizzatore di rete 
SE cade un link, la destinazione non sara quella finale, ma avro uno stack di destinazioni (stack di label)

Vantaggi: 
- fault gestito in maniera distribuita 
- ottimizzatore entra in gioco SOLO in fase di ottimizzatore potendo usare molti tool
- stavolta è presente un red button, cioe spegnere l ottimizzatore e i router seguiranno il best path da standard

Numero di waypoint = numero di reinstradamenti rispetto alla destinazione finale
alle 4 del mattino c è un flush delle policy


come aumentare pero l utilizzo della rete? cambiare come l ottimizzatore funziona
meglio riusciamo a suddividere i flussi, meglio i provider di contenuti possono aumentare l utilizzo e quindi la qualita 
si fa hashing dell header in modo da identificare il singolo stream del cliente facendo ottimizzazione

Onde millimetriche --> 5G