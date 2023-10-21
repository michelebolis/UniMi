I **_feature branch_** sono branch temporanei utilizzati per sviluppare nuove funzionalità o per correggere bug. **Possono essere creati solo a partire dal branch `develop`** e vengono utilizzati per isolare il lavoro su una specifica funzionalità o problema dal resto del codice. Quando il lavoro è completato, il feature branch viene integrato di nuovo nel `develop` tramite un merge. 

In questo modo, è possibile lavorare in modo organizzato su diverse funzionalità o problemi senza interferire tra loro. Per integrare il lavoro svolto in un feature branch nel branch `develop`, è necessario eseguire un merge del feature branch nel `develop`. Ci sono diversi modi di fare ciò, a seconda delle preferenze e delle esigenze specifiche. Un modo semplice di fare il merge è utilizzare il comando `git merge` dalla riga di comando. 
Se il merge non è possibile a causa di conflitti, sarà necessario risolverli manualmente prima di poter completare l’operazione. Una volta risolti i conflitti, sarà necessario creare un nuovo commit per finalizzare il merge.


Per iniziare una feature…

```
$ git checkout develop                  # entra nel branch develop 
$ git branch feature/myFeature          # crea un branch di feature 
$ git checkout feature/myFeature        # entra nel branch appena creato
```

Al termine della feature, integro:

```
$ git checkout develop                  # entra nel branch develop 
$ git merge --no-ff feature/myFeature   # mergia il branch di feature 
$ git branch -d feature/myFeature       # elimina il branch di feature
```

[[Release]]
