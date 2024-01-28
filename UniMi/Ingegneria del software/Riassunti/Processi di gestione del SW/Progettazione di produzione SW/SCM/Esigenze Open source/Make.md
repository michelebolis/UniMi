`make` è uno strumento di build automation che viene utilizzato per automatizzare il processo di compilazione di un progetto. In particolare, `make` viene utilizzato per specificare come ottenere determinati _targets_ (obiettivi), ovvero file o azioni che devono essere eseguite, partendo dal codice sorgente. 

Ad esempio, in un progetto di sviluppo software, un _target_ potrebbe essere il file eseguibile del programma, che viene ottenuto compilando il codice sorgente. `make` segue la filosofia _pipeline_, ovvero prevede l’utilizzo di singoli comandi semplici concatenati per svolgere compiti più complessi.

È supportata la `compilazione incrementale`, ovvero il fatto di compilare solo le parti del progetto che sono state modificate dall’ultima volta, al fine di velocizzare il processo. 
Inoltre, vengono `gestite le dipendenze` tra file, ovvero le relazioni tra i diversi file che compongono il progetto: se un file sorgente dipende da un altro file, make assicura che il file dipendente venga compilato solo dopo che il file da cui dipende è stato compilato. 

Ciò garantisce che il progetto venga compilato in modo coerente e che le modifiche apportate a un file siano considerate correttamente nella compilazione dei file dipendenti.

Svantaggi:
- Tuttavia, make `lavora a un livello molto basso`, il che può rendere facile commettere errori durante la sua configurazione e utilizzo.
- `Non c’è portabilità tra macchine (ambienti) diverse`.