Nel router abbiamo una coda di ingresso per ogni porta di I/O e una coda di uscita per porta porta di I/O
I pacchetti vengono processati da un processo Forwarder e smistati nella specifica coda di uscita, scegliendo in base ad una tabella che in base ad un indirizzo IP destinazione, viene indicata una porta di I/O
Avro tante entry quante sono gli IP conosciuti

IP della sorgente è necessaria ma utilizzata solo dal destinatario

Processo di routing popola la tabella 
è asincrono rispetto al processo di Forwarding
Vediamo il router diviso in 2
- piano dati
- piano controllo

Il processo di routing deve avere una certa conoscenza di tutta la rete in modo tale da costruirsi il cammino minimo anche se nella tabella non troviamo tutto il percoso ma solo il successivo nodo da raggiungere per raggiungere l IP destinazione
Per il cammino minimo come metriche utilizzeremo il delay e il numero di hop 

Il forwarder fa la stessa cosa del Bridge (invece del MAC c è l IP)


Come costruire un processo che fa routing
- [[DV Distance Vector]]
- [[LS Link State]]