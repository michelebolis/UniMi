git e GitFlow come sono stati esposti presentano numerosi vincoli, tra cui:
- la `mancanza di un sistema di autorizzazione granulare`, ovvero la possibilità di assegnare permessi in modo specifico e mirato a diverse funzionalità o risorse. Inoltre, non esiste una distinzione tra diversi livelli di accesso, quindi o si ha accesso completo a tutte le funzionalità o non si ha accesso a niente; --> [[Hosting centralizzato]]
- l’`assenza di code review`, ovvero il processo di revisione del codice sorgente da parte di altri sviluppatori prima che venga integrato nel codice base. --> [[Gerrit]]

Il tool `git request-pull` è un comando di git che serve per formattare e inviare una proposta di modifiche a un repository tramite una mailing list. Il comando crea un messaggio di posta elettronica che chiede al maintainer del repository di “pullare” le modifiche, ovvero di integrarle nel codice base. 
Oggi, questa pratica è stata in molti progetti sostituita dalle `pull request`, che sono richieste di integrazione delle modifiche presentate attraverso un’interfaccia web. Le pull request offrono una serie di vantaggi rispetto alle richieste via email, come una maggiore trasparenza del processo di integrazione, una maggiore efficienza e una maggiore facilità di utilizzo.

La sintassi del comando è la seguente:
`git request-pull [-p] <start> <URL> [<end>]`

Per esempio, i contributori Linux usano questo strumento per chiedere a Linus Torvalds di unire le modifiche nella sua versione. L’output generato mostra file per file le modifiche fatte e i commenti dei commit creati, raggruppati per autore. [[Esigenze Open Source]]

Questo modello è molto più _peer to peer_ delle pull request proposte dai sistemi semi-centralizzati spiegati in seguito.