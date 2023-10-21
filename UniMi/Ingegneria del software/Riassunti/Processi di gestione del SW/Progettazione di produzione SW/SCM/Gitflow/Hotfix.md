Un _hotfix_ è una riparazione veloce di difetti urgenti senza dover aspettare la prossima release. È l’unico caso per cui non si parte da `develop`, ma dall’ultima - o una particolare - versione rilasciata su `master`.

`$ git checkout -b hotfix/CVE-123 master # crea un branch di hotfix`

Quando lo chiudo:

```
$ git checkout master                   # entra nel branch master 
$ git merge --no-ff hotfix/CVE-123      # mergia l'hotfix 
$ git tag -a hotfix/CVE-123             # tagga sul branch master il rilascio 
$ git checkout develop                  # entra nel branch develop 
$ git merge --no-ff hotfix/CVE-123      # mergia l'hotfix 
$ git branch -d hotfix/CVE-123          # elimina il branch di hotfix
```

