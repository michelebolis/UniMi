SE la dimensione del pacchetto è maggiore della dimensione massima del frame (MTU Maximum Transmission Unit), è necessario dividere il payload in un numero di pacchetto con dimensione ridotta, i frammenti.
L'IP del  destinatario si occuperà di ricomporre i frammenti IP con il vantaggio di non sovraccarichiamo i router intermedi

Nel caso di perdita del segmento, l'IP se ne accorge grazie al TCP che ritrasmette i dati MA rimanda tutto, non solo quello che manca perché è il livello 3 che sa quale non è arrivato

[[Esempio Frammentazione]]


