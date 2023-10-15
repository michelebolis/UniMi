Supponiamo di avere una tratta Ethernet con tante stazioni, tanto che il tasso di collisione inizia ad aumentare. Troppe stazioni competono sullo stesso dominio di collisione
Con il Bridge dimezzo la probabilità di accesso al canale
Serve per separare domini di collisione, mettendo in contatto il dominio A con il dominio B

Il Bridge si occuperà di passera le frame destinate al dominio A dal dominio B e viceversa
Il traffico generato all interno dell'area A e B rimangono confinato se la destinazione è nella stessa area

A livello fisico il bridge ha un transciver e un MAC level proprio come una stazione qualsiasi, è un CSMA-CD

Requisito: che il bridge diventa egli stesso una stazione, quindi deve avere una scheda di rete