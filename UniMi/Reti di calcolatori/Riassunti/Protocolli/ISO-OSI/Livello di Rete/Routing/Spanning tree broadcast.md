Consideriamo una rete che usa LS e che è composta da diverse subnet
Con l'algoritmo di spanning tree, ogni router deriva una spanning tree dalla topologia corrente per evitare il loop di frame nella rete globale
Costruire l'albero dei cammini minimi permette, oltre la comunicazione punto-punto, anche il broadcast (facile su CSMA-CD MA non su una rete magliata)

Un router root nello spanning tree viene eletto come root (un modo è eseguendo un algoritmo di elezione o dall indirizzo inferiore) 
Vengono definite le porte associate ad ogni subnet come Root Ports RP (se i nodi sono sui rami  cioe sono sul path per le foglie) o Designated Ports DS
Tutte le porte RP/DS vengono settato in uno stato di forwarding mentre le altre in uno stato di non forwarding

Il numero di porta associato ad ogni subnet è determinato dall'identificato della subnet
Ogni SR ha una Root Port associata che è la porta con il cammino minimo per il root
Per ogni subnet, c è una DP che è la porta con il cammino minimo dalla root
Solo una copia del pacchetto viene mandato in broadcast nella rete

Come evitare i loop se due porte hanno lo stesso costo, sceglie etichetta inferiore