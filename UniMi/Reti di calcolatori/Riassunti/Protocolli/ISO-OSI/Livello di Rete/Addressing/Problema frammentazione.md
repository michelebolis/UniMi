SE la dimensione del pacchetto è maggiore della dimensione massima del frame (MTU Maximum Transmission Unit), è necessario dividere il payload in un numero di pacchetto con dimensione ridotta, i frammenti.
L'IP del  destinatario si occuperà di ricomporre i frammenti IP con il vantaggio di non sovraccarichiamo i router intermedi

Nel caso di perdita del segmento, l'IP se ne accorge grazie al TCP che ritrasmette i dati MA rimanda tutto, non solo quello che manca perché è il livello 3 che sa quale non è arrivato

Formato frammenti
- Il valore del campo Identification (PKT ID) è uguale in tutti i frammenti, in modo che l'IP destinazione li associ allo stesso pacchetto originario 
- Il campo Fragment offset indica la posizione dei dati in ogni frammento rispetto all'inizio del payload (in multipli di 8 bytes)
- Il campo Total length è il numero di bytes del pacchetto originario (inclusi i 20byte di header)
- Il campo M-bit è 1 in ogni frammento e 0 nell'ultimo

[[Esempio Frammentazione]]


