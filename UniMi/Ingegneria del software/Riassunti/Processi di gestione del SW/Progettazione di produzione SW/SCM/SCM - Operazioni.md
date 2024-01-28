Ogni cambiamento è regolato da
- `check-out`: dichiara la volontà di lavorare partendo da una particolare revisione di un artifact
- `check-in`: dichiara la volontà di registrarne una nuova (change-set)
Queste operazioni vengono attivate rispetto a un repository, producendo spostamenti tra il repository e il mio workspace

Il repository mantiene informazioni quali date, tag, versioni, diramazioni/branches, autore…
La repository puo salvare solo le differenze tra una versione e l'altra (In realtà, Git non fa così, perché usa link simbolici: fare il _checkout_ di una specifica versione è istantaneo.)

Puo essere `centralizzata o distribuita` (su qualunque pc c è sia la repo che il workspace. NON vuol dire che tutti hanno la stesso repo)

Nei sistemi di versioning distribuiti c’è il concetto di **hashing**, in modo da identificare file uguali anche se in posizioni diverse. Per confrontare storie diverse si utilizzano gli hash dei file e delle directory.