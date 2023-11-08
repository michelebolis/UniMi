I vari router si scambiano dei vettori di distanze. Con distanza intendiamo la metrica che vogliamo utilizzare come costo per raggiungere un nodo

I costi dei link sono derivanti da un ICMP 
Ipotizziamo che i costi rilevati siano omogenei dai nodi collegati

nelle code di I/O oltre al traffico ci sono anche i pacchetti di controllo del processo di Routing
Tabella nei routing osno chiamate tabella di adiacenza in quanto con gli echo scopre i costi solo dei nodi adiacenti

Vettore delle distanze viene propagato ai nodi adiacenti in modo da trasmettere la conoscenza della rete, inizialmente cio che c è nella tabella di adiacenza (gli indirizzi dei nodi ed i costi associati MA non si dice il link utilizzato in quanto è un info locale inutile)

Ricevendo il distant vector, il nodo scopre nuovi indirizzi raggiungibili (senza comprenderne la topologia) e capisce quanto costa arrivare ai nuovi indirizzi e quindi aggiugendo una nuova entry nella tabella di routing, dato dall indirizzi e dal costo uguale alla somma tra il costo nel distant vector e il costo per raggiungere il nodo da cui proviene il distant vector 
Il diametro della rete influenza il tempo con cui si viene a conoscenza degli indirizzi da un nodo
La conoscenza si diffonde in base al diametro della rete

Quando per un entry gia esistente, si ottiene un costo minore, si cancella la entry e aggiorna costo e link.
E' quindi anche migliorativo

Il Distant Vector viene mandato periodicamente MA l'invio non è sincronizzato tra i link (ed è meglio cosi)
Quindi non è detto che le tabelle di routing convergano immediatamente per il cammino minimo

Problema: errore/guasto in un link
Con il ping periodico viene rilevato il guasto, assegnando un costo infinito (in realta un valore intero massimo che indica infinito)
L'informazione viene quindi propagata attraverso il DV
SE pero un altro nodo A propaga il DV prima che il nodo B mandi il DV con il costo infinito, allora viene rilevato che A riesca a raggiungere il nodo con un costo minore di infinito, e B cambia la sua entry creando un loop in cui il pacchetto rimbalza tra i due nodi (bouncing effect)
Quando ad A poi arrivera DV di B, A aumentera il costo continuamente perche rileva che il costo da B alla destinazione è aumentato (count to infinity)

Questo limite del DV è generato dalla mancanza di sincronizzazione e dalla perdita ...

In realta il bouncing effect si fermera prima dell infinito grazie al raggiungimenro del nodo da un altro nodo

Soluzione: split horizon 
Convenzione che prevede che ogni nodo quando propaga il proprio costo per una destinazione, propaga il costo reale su tutte le adiacenze che non intende usare per raggiungere la destinazione mentre infinito sulle adiacenze che intende utilizzare per raggiungere la destinazione 

Implementazione: [[RIP]]
