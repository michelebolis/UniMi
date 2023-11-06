Supponiamo di avere una tratta Ethernet con tante stazioni, tanto che il tasso di collisione inizia ad aumentare. Troppe stazioni competono sullo stesso dominio di collisione
Con il Bridge dimezzo la probabilità di accesso al canale
Serve per separare domini di collisione, mettendo in contatto il dominio A con il dominio B

Il Bridge si occuperà di passera le frame destinate al dominio A dal dominio B e viceversa
Il traffico generato all interno dell'area A e B rimangono confinato se la destinazione è nella stessa area

A livello fisico il bridge ha un transciver e un MAC level proprio come una stazione qualsiasi, è un CSMA-CD

Requisito: che il bridge diventa egli stesso una stazione, quindi deve avere una scheda di rete

Bridge separa i domini di collisione e a bordo del bridge ci devono essere tante schede quanti domini di collisioni voglio avere 

il bridge ha una tabella di forwarding che contiene, data una stazione, in che dominio si trovano, quindi in che porta dovra usare
Tutti i frame ricevuto sono prima bufferizzati e poi ripetuto come nell'hub tranne dalla porta in cui è arrivato
SE arriva un frame in cui mittente e destinatario sono nella stessa porta, il bridge butta quanto ricevuto

Learning: quando riceve un frame, legge quindi l'indirizzo della sorgente e aggiunta la entry alla sua tabella e se la destinazione non è ancora presente nella tabella, fa broadcast MA senza rimandare sulla linea in cui ha ricevuto (tecnica di fladding)
velocita di learning data dal traffico

Casi limite: aggiunta di un nuovo nodo o cambio di hub a cui era collegato il nodo. Nell'ultimo caso il bridge non lo propaga perche ha una tabella di forwarding sbagliata. 
Viene quindi introdotto un TTL Time To Leave ad ogni entry della tabella ricominciando il learning 