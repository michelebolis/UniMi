- FIFO
Problema della provenienza
SE TCP rileva traffico intenso, potrebbe droppare tutti i pacchetti in arrivo nella coda.
MA poi quando viene rispreso il traffico, ci sarebbe ancora un brust di pacchetti 

- RED Random Early Detection
Cerco di prevenire l insorgenza del problema di traffico a burst
Vengono prese due soglie
- MIN Thrashold
- MAX Thrashhold
Viene definita una LengthAverage
LAVG = alpha^LOLD + (1-alpha)\*LCURRENT
0.5 < alpha < 0.8

Quando arriva un pacchetto, guardo SE la LengthAverage è sotto la min, in tal caso accodo mentre se è sopra la max, allora scarto
SE è tra le due soglie accodo secondo una probabilita p

Droppo casualmente pacchetti in coda
Droppando pacchetti anche se il nuovo pacchetto ci starebbe nella coda, permette di evitare preventivamente il problema del traffico a burst