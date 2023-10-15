Per capire meglio i concetti fondanti del mondo open-source mostriamo in un modo sintetico un confronto tra lo stesso e i metodi di sviluppo tradizionale e agile nel riguardo di svariati concetti:

|Cosa|Tradizionale|Agile|Open source|
|---|---|---|---|
|**Documentazione**|La documentazione è enfatizzata come strumento di controllo qualità e gestione.|La documentazione è de-enfatizzata.|Tutti i manufatti di sviluppo sono disponibili a chiunque, compresi il codice e la documentazione.|
|**Requisiti**|Gli analisti traducono le necessità dell’utente in specifiche software.|Gli utenti fanno parte del team.|Gli sviluppatori spesso sono anche gli utenti.|
|**Assegnamento dello staff**|Gli sviluppatori sono assegnati ad un unico progetto.|Gli sviluppatori sono assegnati ad un unico progetto.|Gli sviluppatori tipicamente lavorano su più progetti con diversi livelli di partecipazione (_impossibile pianificare lo sviluppo_).|
|**Revisione del codice paritaria**|La revisione del codice tra pari è ampiamente accettata ma raramente effettuata.|La _pair programming_ introduce una forma di revisione del codice tra pari.|La revisione del codice è una necessità ed è praticata quasi universalmente.|
|**Tempi di rilascio**|Tante feature in poche release massicce.|Tante piccole release incrementali.|Gerarchia dei tipi di release: _nightly_ (compilazione giornaliera dal branch master), _development_ e _stable_.|
|**Organizzazione**|I team sono gestiti dall’alto.|I team sono auto-organizzati.|I contributori individuali decidono per sé come organizzare la propria partecipazione.|
|**Testing**|Il testing è gestito dallo staff di _Quality Assurance_ (QA), che segue le attività di sviluppo.|Il testing è parte integrante dello sviluppo (TDD).|Il testing e la QA possono essere svolti da tutti gli sviluppatori.|
|**Distribuzione del lavoro**|Parti differenti della codebase sono assegnate a persone differenti.|Chiunque può modificare qualsiasi parte della codebase.|Chiunque può modificare qualsiasi parte della codebase, ma solo i _committer_ possono rendere ufficiali le modifiche.|