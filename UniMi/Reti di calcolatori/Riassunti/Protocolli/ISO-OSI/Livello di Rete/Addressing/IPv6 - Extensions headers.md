- (NH = 0) hop-by-hop options: informazioni per i ruoter visitati durante il path
Informazioni che devono essere esaminate da ogni router che il pacchetto visita

Quando è necessario trasferire pacchetto molto superiori al MTU, i pacchetti che contengono questo header si chiamano jumbograms
Questa option contiene solo il campo jumbo payload length

- (NH = 43) Routing option
Contiene 24 bit di stirct/loose map i quali SE il bit = 1, l'indirizzo specificato deve essere raggiunto in modo diretto, mentre SE bit = 0, l'indirizzo puo essere raggiunto passando da altri indirizzi.
Contiene quindi al massimo 24 indirizzi a cui fa riferimento la mappa

- Fragment: informazioni per permettere alla destinazione di riassemblare il pacchetto (vengono infatti tolti i campi della frammentazione dal formato base del pacchetto)