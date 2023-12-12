Sono tecniche che hanno l'obiettivo di localizzare le anomalie che causano malfunzionamenti rilevati in precedenza e rimuoverle

NON deve essere usato per rilevare malfunzionamenti
L'attività è definita per una programma e un insieme di dati che causano i malfunzionamenti
Si basa sulla riproducibilità del malfunzionamento 
MA va verificato che il malfunzionamento non sia dovuto a specifiche errate

es 
- approccio incrementale: limitare la parte in cui ricercare il difetto
- produzione degli stati intermedi dell'esecuzione del programma

Problemi
- Non sempre è facile stabilire una relazione anomalia-malfunzionamento
- Non esiste una relazione biunivoca tra anomalie e malfunzionamento

- [[Debugging - Tecnica Naive]]
- [[Debugging - Dump di memoria]]
- [[Debugging - Debugging simbolico]]
- [[Debugging - Debugging per prova]]

Altre funzionalità del debugger:
- Gestire la granularità del passo di esecuzione: singolo passo/entrare in una funzione/ drop/reset del frame
- Modificare il contenuto di una variabile o zona di memoria
- Modificare il codice (NON sempre è possibile, potrebbe essere necessaria una ricompilazione)
- Rappresentazioni grafiche dei dati

Automazione debugging: delta/differential debugging