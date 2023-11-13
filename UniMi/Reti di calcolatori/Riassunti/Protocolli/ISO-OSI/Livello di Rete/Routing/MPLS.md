Nella realizzazione delle aree0 si richiede l efficienza dei router
Tecnica MPLS Multi Protocol Label Switching utilizzata nelle aree0
Si ragiona attraverso le etichette, sovrapponendosi all indirizzo IP, MA che vale solo all interno del singolo router
Lo switching lo avevamo conosciuto a livello 2, mappando una porta di ingresso in una di uscita

MPLS agisce sulla parte del router che si occupa del forwarder, facendolo operare come uno switch
Trasformo il router in un apparato che fa forwarding SENZA curarsi del routing

il LS continua ad essere a bordo del router, MA è funzionale a far funzionare il router come uno switch
Il router di gateway dell area0 si chiamano Area Border Router: qui si compie la trasformazione da LS a MPLS


Router non convenzionale (MPLS)
OSPF è ancora li
differenze:
- le informazioni di routing popolano anche la Label switching table
- l'IP header e l'IP payload vengono trasformati in un MPLS pacchetto. Questo avviene tramite tunneling, incapsulando quindi il pacchetto IP
- labeling: assegnamento della label al pacchetto
- Gestisco le code in base all etichetta

Il ruoter ragiona solo in base alla porta di ingresso - etichettaRilevata - etichettaNuova - porta di uscita. Ci sara una tabella per ogni porta
l'unica cosa che si porta dietro per tutta la rete sono i QoS

Le tabelle inizialmente NON sono vuote, ma i router si ritrovano le tabelle gia costruite da un processo centralizzato (forma di designated router)

MPLS formato pacchetto
l'header di MPLS contiene
- label su 20bit
- CoS Class of Service 
- TTL time to leave

In questo modo otteniamo aree0 il piu veloce possibili perche non si deve ispezionare l IP MA viene fatto tutto piu velocemente come se fosse uno switch