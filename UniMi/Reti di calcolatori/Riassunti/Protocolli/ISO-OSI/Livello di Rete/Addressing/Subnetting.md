NET ID - SubNet ID - Host ID
L'organizzazione in SubNet non è definita da uno standard, ma è demandata al livello IP che sceglie quanti bit degli host ID demandare al SubNet ID
Per discriminare SubNet e host id, aggiungo ad ogni entry nella tabella di routing la SubNet Mask, tanti 1 quanti bit sono usati dal SubNet ID. Facendo l'AND tra il mio indirizzo e la mask, maschero i bit dell'host id

es 16bit NET ID - 6bit SubNet ID - 10 Host ID
11111111 11111111 111111 0000000000 = /22 cioè ha bisogno di 22 1

130.50.15.6
xxx . xxx . 000011 11.00000110
111..111. 111111 00.00000000

Come risultato rimarranno solo i bit del SubNet: 000011 = SubNet ID 3

Quindi: 
- Viene analizzato il NetID
- SE è lo stesso della rete a cui è collegato il router, manda li il pacchetto
	- Viene controllato il SubNet ID
		- Viene controllatol Host ID

Vantaggio: disaccoppia i router associati ad una rete con le funzioni di routing della rete globale
Svantaggio: complica le tabelle di routing