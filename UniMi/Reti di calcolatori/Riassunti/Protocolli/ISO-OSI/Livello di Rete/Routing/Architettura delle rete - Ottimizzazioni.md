SE aree0 molto grandi, avremo grandi costi di traffico e computazione
Un nodo viene eletto come `Designated Router` per fare OSPF in modo che il costo computazione sia centralizzato. QUINDI tutti i router della rete non si scambiano in flooding ma mandano i LS solo al Designated Router
Il Designated Router propagherà poi le tabelle specifiche per ogni nodo
- Problema di `vulnerabilità della rete` 
	- il `Designated Router viene duplicato` per sicurezza
- Problema di `convergenza del traffico` verso il Designated Router 
	- i `link sono robusti e veloci` verso il Designated Router

Oggi si sposta la funzione di routing all'interno di un datacenter (SDN SW Defined Networking)
In questo modo disaccoppio piano dati e di controllo. I nodi fanno solo forwarding
OPEN FLOW: protocollo che regola la comunicazione tra ogni apparato di rete e il "datacenter" associato