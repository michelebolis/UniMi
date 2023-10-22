Supponiamo di avere una tratta Ethernet con tante stazioni, tanto che il tasso di collisione inizia ad aumentare. Troppe stazioni competono sullo stesso dominio di collisione
Con il Bridge dimezzo la probabilità di accesso al canale
Serve per separare domini di collisione, mettendo in contatto il dominio A con il dominio B

Il Bridge si occuperà di passera le frame destinate al dominio A dal dominio B e viceversa
Il traffico generato all interno dell'area A e B rimangono confinato se la destinazione è nella stessa area

A livello fisico il bridge ha un transciver e un MAC level proprio come una stazione qualsiasi, è un CSMA-CD

Requisito: che il bridge diventa egli stesso una stazione, quindi deve avere una scheda di rete

Bridge separa i domini di collisione
MAC solo presente nei nodi e nel bridge tra gli hub
quindi a bordo del bridge ci devono essere tante schede quanti domini di collisioni voglio avere 

il bridge ha una tabella di forwarding che contiene, data una stazione, in che dominio si trovano, quindi in che porta dovra usare
ATT il bridge non si deve comportare come un hub, ma deve fare store and forward 
SE arriva un frame in cui mittente e destinatario sono nella stessa porta, il bridge butta quanto ricevuto

Problema della gestione della tabella: fa learning e se non sa dove sia, fa broadcast MA senza rimandare sulla linea in cui ha ricevuto (tecnica di fladding)
velocita di learning data dal traffico

Casi limite: aggiunta di un nuovo nodo o cambio di hub a cui era collegato il nodo. Nell'ultimo caso il bridge non lo propaga perche ha una tabella di forwarding sbagliata. Viene quindi introdotto un TTL Time To Leave ricominciando il learning 

Perche fare come il bridge per il broadcast sarebbe sbagliato? Dato che la scheda con CS e collision detection, non saprà mai se avra colliso