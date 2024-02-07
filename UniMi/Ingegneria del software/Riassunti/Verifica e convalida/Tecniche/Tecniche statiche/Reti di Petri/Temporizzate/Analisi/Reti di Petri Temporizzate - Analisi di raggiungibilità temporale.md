Analisi di raggiungibilità consiste nella enumerazione degli stati finiti raggiungibili
Problemi: 
- lo scatto di una transizione puo produrre infiniti stati che si differenziano tra loro per il tempo associato ai gettoni prodotti 
- la rete puo evolvere all'infinito

Non si può usare l'albero di copertura come nelle reti limitate

[[Reti di Petri Temporizzate - Stati simbolici]]
[[Reti di Petri Temporizzate - Albero di raggiungibilità temporale]]

Eseguendo l'algoritmo questo `NON termina` in quanto non abbiamo una forma normale, quindi non possiamo confrontare stati per capire se li abbiamo gia visitati
Possiamo comunque verificare delle proprieta entro un limite finito di tempo: `bounded invariance` e `bounded liveness`

[[Reti di Petri Temporizzate - Grafo aciclico]]