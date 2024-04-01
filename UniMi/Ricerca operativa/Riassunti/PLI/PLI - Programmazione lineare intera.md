Esistono diverse classi di problemi di ottimizzazione con variabili discrete
- IP Integer Programming: variabili vincolate ad assumere valori interi
- BP Binary Programming: variabili vincolate ad assumere solo due valori
- MIP Mixed Integer Programming: alcune variabili discrete e alcune continue
- CO Combinatorial Optimization: delle variabili indicano gli elementi dell insieme 

Noi consideriamo solo modelli lineari `PLI`

NON si puo calcolare la derivata, NON si puo considerare il vertice del poliedro perche potrebbe avere coordinate non intere
Per ottimizzare nel discreto possiamo
- selezionare buone formulazioni lineari e migliorarle fino a poterle risolvere un problema di PLI come PL
- scomporre il problema in sotto problemi piu piccoli e piu facili
- eseguire una enumerazione implicita delle soluzioni

[[PLI - Ottimalità]]

Tecniche principali
- risolvere all'ottimo un [[PLI - Rilassamento|rilassamento]] $R$ di $P$
- trovare una soluzione ammissibile al [[PLI - Problema duale|duale]] $D$ di $P$

OSS nel discreto il teorema della dualità in forma debole resta vero mentre quello in forma forte in generale non è piu vero

[[PLI - Cutting Planes]]
[[PLI - Branch and bound]]
[[Modelli di ottimizzazione discreta]]