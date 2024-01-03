I vari router si scambiano dei `vettori di distanze`. 
Con distanza intendiamo la metrica che vogliamo utilizzare come costo per raggiungere un nodo

I costi dei link sono derivanti da un ICMP 
Ipotizziamo che i costi rilevati siano omogenei dai nodi collegati

Nelle code di I/O oltre al traffico ci sono anche i pacchetti di controllo del processo di Routing
Tabella nei routing sono chiamate tabella di adiacenza in quanto con gli echo scopre i costi solo dei nodi adiacenti

Il vettore delle distanze viene propagato ai nodi adiacenti in modo da trasmettere la conoscenza della rete, inizialmente ciò che c'è nella tabella di adiacenza (gli indirizzi dei nodi ed i costi associati MA non si dice il link utilizzato in quanto è un info locale inutile)

Ricevendo il distant vector, il nodo scopre nuovi indirizzi raggiungibili (senza comprenderne la topologia) e capisce quanto costa arrivare ai nuovi indirizzi e quindi aggiungendo una nuova entry nella tabella di routing, dato dall'indirizzi e dal costo uguale alla somma tra il costo nel distant vector e il costo per raggiungere il nodo da cui proviene il distant vector 
Il diametro della rete influenza il tempo con cui si viene a conoscenza degli indirizzi da un nodo
La conoscenza si diffonde in base al diametro della rete

Quando per un entry gia esistente, si ottiene un costo minore, si cancella la entry e aggiorna costo e link.
E' quindi anche migliorativo

Il Distant Vector viene mandato periodicamente MA l'invio non è sincronizzato tra i link (ed è meglio cosi)
Quindi non è detto che le tabelle di routing convergano immediatamente per il cammino minimo

[[Split Horizon]]
Implementazione: [[RIP]]
