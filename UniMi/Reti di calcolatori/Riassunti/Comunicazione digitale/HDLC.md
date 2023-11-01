Protocollo a livello data link che definisce il formato standard del frame:
- flag 8 bit

Tra il livello 2 al livello 1 il trasmettitore aggiunge una sequenza di bit all'inizio e alla fine, flag formata da 8 bit: 0 111 111 0
In idle il ricevitore legge tutti 1 o tutti 0, quindi quando riceve il flag il ricevitore inizia a sincronizzare il proprio clock in quanto sa che dopo lo 0 si deve aspettare 6 1 e poi lo 0.
A livello fisico dopo aver ricevuto lo 0, processo bit a bit gli 1 contandoli con un contatore, sia all'inizio che alla fine 

Il ricevitore sa che la sequenza finale di flag non è il payload grazie al bit staffing che aggiunge nelle sequenze che corrispondono al flag uno 0 dopo 5 1 (il ricevitore aggiunge un delay di un bit)
Il trascriver del ricevitore processa e toglie le flag all'inizio e alla fine, non arrivando quindi al 2o livello

- Indirizzo 8/16 bit
- Controllo 8/16 bit
	- 0
	- V(S) 3 bit sequence del sender (prof dice 4)
	- P/F
	- V(R) 3 bit sequence del receiver (prof dice 4)
- Frame check sequence 16/32 bit
- Flag 8 bit

Il protocollo per la correttezza lo mette al livello 2 quando so che il canale è molto inaffidabile 
Mettere HTLC al livello 2 costa molto in termini di tempo
Ora il tasso di errore del canale è diminuito, lasciando che se ne occupi il livello 4
Oggi usiamo un livello 2 affidabile sul canale radio e wireless 