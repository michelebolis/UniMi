Il `refactoring` consiste nel `cambiare il design del codice senza cambiarne il funzionamento`
Durante il refactoring è opportuno rispettare le seguenti regole:
- `le modifiche al codice non devono modificare le funzionalità`: il refactoring DEVE essere invisibile al cliente;
- `non possono essere aggiunti test` aggiuntivi rispetto alla fase verde appena raggiunta.

Se la fase di refactoring sta richiedendo troppo tempo allora è possibile fare rollback all’ultima versione verde e **pianificare meglio** l’attività di refactoring. 
Vale la regola del `do it twice`: il secondo approccio a un problema è solitamente più veloce e migliore.

Spesso le motivazioni dietro un refactoring sono:
- `precedente design molto complesso e poco leggibile`, a causa della velocità del passare ad uno _scenario verde_;
- `preparare il design di una funzionalità` che non si integra bene in quello esistente; dopo aver raggiunto uno _scenario verde_ in una feature, è possibile che la feature successiva sia difficile da integrare. In questo caso, se il _refactoring_ non è banale è bene fermarsi, tornare indietro e evolvere il codice per facilitare l’iterazione successiva (**design for change**).
- presenza di [[Debito tecnico]] su lavoro fatto in precedenza, ovvero debolezze e “scorciatoie” che ostacolano notevolmente evoluzioni future.
- [[Code smell]]

