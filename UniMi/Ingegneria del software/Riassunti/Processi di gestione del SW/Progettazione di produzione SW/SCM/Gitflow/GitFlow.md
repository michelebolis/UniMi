GitFlow è una tecnica di organizzazione dei branch e delle repository che prevede la creazione sia di diversi tipi di branch a vita limitata che il loro _merge_ guidato.

I branch e i tipi di branch previsti da GitFlow sono:
- branch master;
- branch develop;
- feature branches;
- release branches;
- hotfix branches.

In GitFlow, ci sono due branch che hanno una durata più lunga rispetto ai branch temporanei utilizzati per lavorare su specifiche funzionalità o correzioni di bug:
- **`master`**: contiene le versioni stabili del codice sorgente, pronte per essere consegnate o rilasciate al cliente o al pubblico. Queste versioni sono considerate _affidabili_ e _testate_, quindi possono essere utilizzate in produzione;
- **`develop`**: è il ramo di integrazione in cui vengono integrati i contribuiti di tutti i gruppi; è anche il punto di partenza degli altri tipi di branch.

Al termine di ogni rilascio, il contenuto del branch `develop` viene integrato nel branch `master`, che rappresenta la versione stabile del codice. Le _versioni notturne_, invece, sono versioni di sviluppo che vengono rilasciate periodicamente e contengono le ultime modifiche apportate al codice. Esse vengono create partendo dal branch `develop`, che rappresenta il punto di integrazione di tutti i contributi dei gruppi di lavoro.

[[Feature branch]]

Di default, git risolve il merge di due branch con la stessa storia banalmente eseguendo il _fast forward_, ovvero spostando il puntatore del branch di destinazione all’ultimo commit del branch entrante.

In GitFlow è preferibile esplicitamente **disabilitare il fast forward** (con l’opzione `--no-ff`) durante il merge in `develop` in quanto è più facile distinguere il punto di inizio e il punto di fine di una feature.

Usando git è anche possibile eseguire in fase di merge lo _squashing_ dei commit, ovvero la fusione di tutti i commit del branch entrante in uno solo. Questa operazione è utile per migliorare la leggibilità della history dei commit su branch grossi (come `develop` o `master`) ma il suo uso in GitFlow è opinabile: il prof. Bellettini consiglia di non utilizzarlo, in modo da mantenere i commit originali.


In git, i tag sono etichette che possono essere applicate a un commit per segnalarne l’importanza o per marcare un punto specifico dello storico del repository. 
Un **tag è un puntatore costante al commit** a cui è stato applicato, quindi non cambia mai e permette di fare riferimento in modo stabile a una versione specifica del codice. Al contrario, i branch sono puntatori dinamici che vanno avanti nel tempo, seguendo l’evoluzione del codice attraverso i nuovi commit

In GitFlow, le release sono versioni stabili del codice che vengono rilasciate al pubblico o al cliente. Ogni release viene creata partendo dal branch `develop` e viene gestita come un branch a sé stante, che viene chiuso una volta che tutte le modifiche previste sono state integrate. 

Al contrario, le feature sono branch temporanei utilizzati per sviluppare nuove funzionalità o per correggere bug. È possibile avere più feature aperte contemporaneamente, ma solo una release rimanere aperta in un dato istante.

[[Hotfix]]
[[Gitflow - limiti]]

