La struttura di Internet è una `rete di reti`: collezione di `AS Atonomous System` i quali hanno una topologia che prevede un `area0 / backbone` (OSPF, MPLS) collegate ad altre `sottoaree` (RIP / OSPF). 
`NON ci sono collegamenti tra sottoaree`

Le varie aree0 sono collegate a Internet Backbone 
- Tier 1: Internet Backbone -> [[BGP]]
- Tier 2: AS gateway della rete regionale -> router backbone [[MPLS]]
- Tier 3: reti di accesso / reti periferiche -> [[DV - Distance Vector|DV]] o [[LS - Link State|LS]]

![[Pasted image 20231219133313.png|600]]

![[Pasted image 20231219132229.png|600]]

[[Architettura delle rete - Ottimizzazioni]]


