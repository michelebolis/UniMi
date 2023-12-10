Supponiamo di avere una tratta Ethernet con tante stazioni, tanto che il tasso di collisione inizia ad aumentare. Troppe stazioni competono sullo stesso dominio di collisione

Il bridge è un dispositivo che serve per separare domini di collisione, mettendo in contatto il dominio A con il dominio B, in particolare permette di far i frame destinati al dominio A dal dominio B e viceversa e allo stesso tempo, il traffico generato all interno dell'area A e B rimangono confinato se la destinazione è nella stessa area.
Con il Bridge quindi dimezzo la probabilità di accesso al canale

A livello fisico il bridge ha un trascriver e un MAC level proprio come una stazione qualsiasi, è un CSMA-CD

Requisito: deve avere una scheda di rete
Bridge separa i domini di collisione e a bordo del bridge ci devono essere tante schede quanti domini di collisioni voglio avere 

Il bridge ha una tabella di forwarding che contiene, data una stazione, in che dominio si trovano, quindi che porta dovra usare
Tutti i frame ricevuto sono prima bufferizzati e poi il frame viene ripetuto, come nell'hub, tranne dalla porta in cui è arrivato (`Fladding`)
SE arriva un frame in cui mittente e destinatario sono nella stessa porta, il bridge butta quanto ricevuto

Fase di Learning: quando riceve un frame, legge l'indirizzo della sorgente e aggiunte la entry alla sua tabella e SE la destinazione non è ancora presente nella tabella, fa broadcast MA senza rimandare sulla linea in cui ha ricevuto 
La velocita di learning dipende dal traffico

Problema: aggiunta di un nuovo nodo o cambio di hub a cui era collegato il nodo, il bridge non lo propaga perche ha una tabella di forwarding sbagliata. 
Viene quindi introdotto un TTL Time To Leave ad ogni entry della tabella al cui scadere viene riavviata la fase di learning 