Per modello intendiamo una famiglia di processo di sviluppo che si distinguono nel modo in cui organizzano le fasi del ciclo di vita del SW

Modelli
- prescrittivi: da un modo per procedere, quella giusta (spesso in realtà incompleti)
- descrittivi: rappresentano una situazione prendendone solo alcuni aspetti perché non direttamente utilizzabili 

Modelli
- [[Modelli sequenziali]]: le varie fasi sono poste in un ordine prestabilito
- [[Modelli iterativi]]: evoluzione dei modelli sequenziali in cui è permessa la ripetizione di una o piu fasi
- [[Modelli incrementali]]: modelli in cui nelle iterazioni viene inclusa la consegna, permettendo così di rilasciare componenti di volta in volta


- implementazione iterativa: dopo aver raccolto le specifiche, si eseguono le fasi di modularizzazione e identificazione di sottosistemi e si ripetono fasi di coding ed integrazione
- sviluppo incrementale
	- viene esteso a tutte le fasi, specifiche comprese, riconoscendo la variabilità delle richieste
	- la fase di manutenzione in senso stretto sparisce diventando semplice riciclo

Problemi con i modelli incrementali
- il lavoro di planning viene complicato in quanto lo stato del processo è meno visibile e bisogna pianificare tutte le iterazioni
- si riconosce che bisogna rimettere mano a ciò che si è fatto MA il sistema potrebbe non convergere, non arrivando mai a un risultato che consegno e che non lo tocco piu
- cosa è un iterazione e quanto dura?
	- rischio di voler mettere troppo nella prima iterazione
	- rischio di overhead dovuto a troppe iterazioni
	- rischio di avere un eccessivo overlapping tra le iterazioni in quanto non si hanno feedback dell'utente

[[Metodologie agili]]