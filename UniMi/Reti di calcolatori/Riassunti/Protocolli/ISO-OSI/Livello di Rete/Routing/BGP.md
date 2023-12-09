BGP Border G Protocol = Path Vector

Assomiglia a DV
Vengono propagati vettori delle distanze senza fare flooding.
In questo caso i DV contengono anche per ogni destinazione, il costo e il cammino per raggiungere la destinazione (per evitare count to infinity)

Ha un costo inferiore del LS MA i nodi devono conoscere il Path a configuration time o run time
BGP funziona SOLO tra router di Tier 1

BGP funzionalmente è a livello 3 MA in realtà nell'implementazione è un protocollo a livello 7 utilizzando TCP