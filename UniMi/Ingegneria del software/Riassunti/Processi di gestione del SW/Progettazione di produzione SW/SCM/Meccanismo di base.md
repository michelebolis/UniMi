Qualunque sistema si usi, occorre prendere decisioni importanti che influenzano la replicabilità della produzione
- Si traccia l'evoluzione anche di componenti esterni dal nostro controllo? (es librerie, compilatori)
- Si archiviano i file che costituiscono e costruiscono il prodotto?
Solitamente NO in quanto troppo costo e poco pratico, perdendo la perfetta replicabilità

### Operazioni
Ogni cambiamento è regolato da
- check-out: dichiara la volontà di lavorare partendo da una particolare revisione di un artifact
- check-in: dichiara la volontà di registrarne una nuova (change-set)
Queste operazioni vengono attivate rispetto a un repository, producendo spostamenti tra il repository e il mio workspace

Il repository mantiene informazioni quali date, tag, versioni, diramazioni/branches, autore…
La repository puo salvare solo le differenze tra una versione e l'altra (In realtà, Git non fa così, perché usa link simbolici: fare il _checkout_ di una specifica versione è istantaneo.)

Puo essere centralizzata o distribuita (su qualunque pc c è sia la repo che il workspace. NON vuol dire che tutti hanno la stesso repo)

Nei sistemi di versioning distribuiti c’è il concetto di **hashing**, in modo da identificare file uguali anche se in posizioni diverse. Per confrontare storie diverse si utilizzano gli hash dei file e delle directory.

### Regolamento del lavoro concorrente
Quando il repository è condiviso da un gruppo di lavoro, nasce il problema di gestirne l'accessi concorrente
- Modello pessimistico RCS: accesso agli artifact con mutua esclusione attivando un lock al check-out. Questo approccio non puo funzionare nell'open-source
- Modello ottimistico CVS: il sistema si disinteressa del problema e fornisce supporto per le attività di merge di change-set paralleli potenzialmente conflittuali
	E' possibile regolarlo parzialmente tramite rami paralleli di sviluppo, branch. In Git, l’uso dei branch è talmente comune che a volte è necessario introdurre delle politiche (come GitFlow) sul loro utilizzo.

[[GitFlow]]