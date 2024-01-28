Lo scopo di creare una release è **cristallizzare l’insieme delle funzionalità** presente sul branch `develop` all’inizio di essa dedicandosi solo alla sistemazione degli errori o alle attività necessarie per il deploy (modifica del numero di versione, …). L’insieme delle funzionalità rilasciate è quello presente sul branch `develop` al momento di inizio di una release.

I bug fix possono essere ri-mergiati in `develop`, anche utilizzando la funzionalità **cherry-pick** di git; essa permette di selezionare un commit specifico da un ramo e applicarlo in un altro ramo. 

Ad esempio, se si ha un ramo di sviluppo (“`develop`”) e un ramo di release (“`release`”), è possibile utilizzare il cherry-pick per selezionare solo i commit che contengono bugfix e applicarli al ramo di release, senza dover fare un merge di tutto il ramo di sviluppo. 

Ciò può essere utile in casi in cui si vuole mantenere la stabilità del ramo di release, includendo solo i bugfix considerati essenziali per la release.

Per iniziare una nuova release è sufficiente creare un nuovo branch da `develop`:

`$ git checkout -b release/v1.2.3 develop`

Al termine della creazione della release, è necessario fare il merge della release nel branch `master` e nel branch `develop`. Il merge in `master` rappresenta il rilascio della nuova versione del codice, che diventa disponibile per il pubblico o per il cliente. Il merge in `develop`, invece, integra le modifiche apportate durante la creazione della release nel branch di sviluppo, in modo che siano disponibili per le release future. 
In questo modo, è possibile gestire in modo organizzato il ciclo di vita del codice e il flusso di lavoro.

```
$ git checkout master               # entra nel branch master 
$ git merge --no-ff release/v1.2.3  # mergia la feature 
$ git tag -a v1.2.3                 # tagga sul branch master il rilascio 
$ git checkout develop              # entra nel branch develop 
$ git merge --no-ff release/v1.2.3  # mergia la feature 
$ git branch -d release/v1.2.3      # elimina il branch della feature
```
