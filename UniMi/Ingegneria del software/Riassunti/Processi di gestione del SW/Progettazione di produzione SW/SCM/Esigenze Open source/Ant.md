Ant nasce in Apache per supportare il progetto Tomcat. 
Data una **definizione in XML** della struttura del progetto e delle dipendenze invocava comandi programmati tramite classi Java per compilare il progetto.

Il vantaggio è che `Java offre un livello d’astrazione sufficiente a rendere il sistema di build portabile su tutte le piattaforme`.

Non solo compila, ma fa anche `deployment`. 
Il `deployment` consiste nell’installare e configurare un’applicazione o un sistema su uno o più server o ambienti di esecuzione. 
Nel contesto di Ant, il deployment può includere l’invocazione di comandi per copiare i file del progetto sui server di destinazione, configurare le impostazioni di sistema o dell’applicazione, avviare o fermare servizi o processi, e così via. In questo modo, Ant può essere utilizzato non solo per compilare il progetto, ma anche per distribuirlo e rendere disponibile l’applicazione o il sistema ai suoi utenti.

I target possono avere dipendenze da altri target. I target contengono task che fanno effettivamente il lavoro; si possono aggiungere nuovi tipi di task definendo nuove classi Java.