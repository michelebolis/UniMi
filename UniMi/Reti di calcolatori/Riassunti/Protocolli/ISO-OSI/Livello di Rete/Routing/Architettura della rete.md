La struttura di Internet è una rete di reti: topologia che prevede un area0 / backbone (OSPF, MPLS) collegate ad altre sottoaree (RIP / OSPF). NON ci sono collegamenti tra sottoaree

SE aree0 molto grandi, avremo grandi costi di traffico e computazione
Un nodo viene eletto come Designated Router per fare OSPF in modo che il costo computazione sia centralizzato. QUINDI tutti i router della rete non si scambiano in flooding ma mandano i LS solo al Designated Router
Il Designated Router propagherà poi le tabelle specifiche per ogni nodo
- Problema di vulnerabilità della rete -> il Designated Router viene duplicato per sicurezza
- Problema di convergenza del traffico verso il Designated Router -> i link verso il Designated Router devono essere robusti e veloci 

Oggi si sposta la funzione di rounting all'interno di un datacenter (SDN SW Defined Networking)
In questo modo disaccoppio piano dati e di controllo. I nodi fanno solo forwarding
OPEN FLOW: protocollo che regola la comunicazione tra ogni apparato di rete e il "datacenter" associato

Internet: collezione di AS Atonomous System
Le varie aree0 sono collegate a Internet Backbone 
- Tier 1: Internet Backbone -> [[BGP]]
- Tier 2: AS gateway della rete regionale -> router backbone [[MPLS]]
- Tier 3: reti di accesso / reti periferiche -> [[DV - Distance Vector|DV]] o [[LS - Link State|LS]]

![[Pasted image 20231219133313.png|600]]
![[Pasted image 20231219132229.png|600]]