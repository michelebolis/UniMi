`Gerrit` è un **sistema di review** del codice sviluppato internamente da Google per gestire i progetti interni; si basa sul concetto di “peer review”: tutti gli sviluppatori sono autorizzati a fare review delle proposte di modifica di qualsiasi zona di codice.

Pensa git come due repository, uno in cui possono fare fetch e un altro in cui si possa fare push e su cui verranno fatte le review.

Nel processo di review di Gerrit, i **developer** possono sottoporre proposte di cambiamento utilizzando un `sistema di “patch”` che descrive le modifiche apportate al codice. 
I **reviewer**, ovvero gli altri sviluppatori del progetto, possono quindi esaminare le patch e decidere se accettarle o rifiutarle. Una volta che una patch ha ricevuto un numero sufficiente di review positivi, viene automaticamente integrata nel **repository principale autoritativo** in cui tutti hanno accesso in sola lettura.

Gerrit obbliga a strutturare le modifiche (_changeset_) in un unico commit (`tecnica squash`) al momento dell’accettazione. 
Ciò significa che tutte le modifiche apportate devono essere fuse in un unico commit, in modo da rendere più facile la gestione del repository. 
Al momento della review, invece, le modifiche rimangono separate in versioni singole, ovvero ogni modifica viene presentata come un commit separato, in modo che i reviewer possano esaminarle più facilmente.

Il `verifier` è uno strumento o un processo che viene utilizzato in Gerrit per verificare che le modifiche proposte siano corrette e funzionino come dovrebbero. 
In particolare, il verifier scarica la patch, la compila, esegue i test e controlla che ci siano tutte le funzioni necessarie. 
Se il verifier rileva dei problemi, può segnalarli al team di sviluppo perché vengano corretti prima che la patch venga accettata.

Una volta verificata, una proposta di modifiche deve essere anche approvata. 
L’`approver` deve determinare la risposta alle seguenti domande riguardo la proposta di modifiche (questa figura ha una conoscenza piu generale del progetto e dei suoi scopi, decidendo se sia coerente):
- _è valida per lo scopo del progetto?_
- _è valida per l’architettura del progetto?_
- _introduce nuove falle nel design che potrebbero causare problemi in futuro?_
- _segue le best practices stabilite dal progetto?_
- _è un buon modo per implementare la propria funzione?_
- _introduce rischi per la sicurezza o la stabilità?_

Se l’approver ritiene che la proposta di modifiche sia valida, può approvarla scrivendo “LGTM” (acronimo di _“Looks Good To Me”_) nei commenti della pull request.