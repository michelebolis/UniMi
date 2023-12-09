- Unicast
	- Classe A: 7 bit per NET ID e 24 bit per Host ID
	- Classe B: 14 bit per NET ID e 16 bit per Host ID
	- Classe C: 21 bit per NET ID e 8 per Host ID
- Multicast: Classe F: 28 bit per Multicast address
- Reserved: Classe E

Casi particolare
- NetID di soli 0: indica la stessa rete del mittente
- Indirizzo a tutti 1: broadcast nella stessa rete del mittente
- HostID di soli 1: broadcast sulla rete destinazione
- Un indirizzo di classe A di soli 1 è utilizzato per il test, loopback address

La gerarchia è utile per i router intermedi di rete che non devono quindi ispezionare tutti i 32 bit, ma SOLO il NET ID
Grazie alla gerarchia nelle tabelle di instradamento dei router intermedi conservo solo i NET ID