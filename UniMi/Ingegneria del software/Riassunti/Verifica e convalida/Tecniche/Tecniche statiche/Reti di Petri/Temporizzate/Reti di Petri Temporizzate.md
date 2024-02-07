Contesto: `sistemi Hard Real-time`
Il tempo è un fattore essenziale in moltissime applicazioni
Hard Real time significa che bisogna soddisfare dei vincoli temporali senza errori 

L'analisi stocastica potrebbe non essere sufficiente in questi casi quindi la capacita di avere modelli deterministici è complementare e non alternati ai modelli stocastici

Modelli temporali
Per aggiungere il tempo deterministico alle reti di Petri, esistono diverse possibilità
- [[Reti di Petri Temporizzate - Tempo sui posti]]
- [[Reti di Petri Temporizzate - Tempo sulle transizioni]]

[[Reti di Petri Temporizzate - Time Basic]] nets (Ghezzi)

Tempo come concetto derivato
Vediamo il tempo come variabile associata ai gettoni
I predicati determinano la possibilità di scatto di una transizione a partire dai valori dei gettoni
Le azioni determinano i valori dei gettoni creati

Le azioni DEVONO produrre lo stesso valore per i chronos di tutti i gettoni creati e devono essere minori dei valori dei chronos dei gettoni rimossi

Semantiche temporali nelle ER nets
WTS = chronos + assiomi 1, 3
MWTS = chronos + assiomi 1, 2, 3
STS = chronos + assiomi 1, 2, 3, 4, 5 

[[Reti di Petri Temporizzate - HLTPN]]
[[Reti di Petri Temporizzate - Analisi di raggiungibilità temporale]]
