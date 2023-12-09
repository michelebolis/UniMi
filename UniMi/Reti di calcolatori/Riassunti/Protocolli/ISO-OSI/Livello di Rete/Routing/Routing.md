Nel router abbiamo una coda di ingresso per ogni porta di I/O e una coda di uscita per porta porta di I/O
I pacchetti vengono processati da un processo Forwarder e smistati nella specifica coda di uscita, scegliendo in base ad una tabella di instradamento permette di ruotare ogni pacchetto ad ogni altro network in Internet in base ad un indirizzo IP destinazione, indicando una porta di I/O
Il processo di routing che popola la tabella è asincrono rispetto al processo di Forwarding

Come un pacchetto viene inviato in una rete IP standard
Alla ricezione del pacchetto da una linea di input, il router legge l'IP destinazione nell'header per determinare il NetID utilizzando la maschera
Usa il NetID per determinare la porta di uscita grazie alla tabella di instradamento
Il campo ToS nell'header viene passato al classificatore di pacchetti che determina la coda e le regole di scheduling da applicare al pacchetto. Cio determina la porta di uscita da utilizzare per mandare il pacchetto al prossimo hop.
Una regola di coda e scheduling vengono usate per ogni classe per assicurare che i requisiti di [[QoS]] vengano rispettati

Vediamo il router diviso in 2:
- piano dati
- piano controllo

Il processo di routing deve avere una certa conoscenza di tutta la rete in modo tale da costruirsi il cammino minimo anche se nella tabella non troviamo tutto il percorso ma solo il successivo nodo da raggiungere per raggiungere l'IP destinazione
Per il cammino minimo come metriche utilizzeremo il delay e il numero di hop.

[[Architettura della rete]]