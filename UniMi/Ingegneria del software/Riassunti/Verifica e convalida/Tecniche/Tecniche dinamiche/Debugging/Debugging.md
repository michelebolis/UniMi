Il `debugging` l'insieme delle tecniche che ha l'obiettivo di `localizzare e rimuovere le anomalie che causano malfunzionamenti rilevati in precedenza`. Richiede un programma e un `malfunzionamento NOTO e riproducibile` (NON deve essere usato per rilevare malfunzionamenti).

L'attività è definita per una programma e un insieme di dati che causano i malfunzionamenti 
MA va verificato che il malfunzionamento non sia dovuto a specifiche errate

Approcci:
- `approccio divide et impera`: limitare la parte di codice in cui ricercare l'anomalia (es breakpoint)
- `produzione degli stati intermedi` dell'esecuzione del programma es esecuzione passo-passo

Problemi
- Non sempre è facile stabilire una relazione anomalia-malfunzionamento
- `Non esiste una relazione biunivoca tra anomalie e malfunzionamento`
- `la correzione di un'anomalia potrebbe introdurre altre anomalie`

[[Debugging - Tecnica Naive]]
[[Debugging - Dump di memoria]]
[[Debugging - Debugging simbolico]]
[[Debugging - Debugging per prova]]

Altre funzionalità del debugger:
- Gestire la granularità del passo di esecuzione: singolo passo/entrare in una funzione/ drop/reset del frame
- Modificare il contenuto di una variabile o zona di memoria
- Modificare il codice (NON sempre è possibile, potrebbe essere necessaria una ricompilazione)
- Rappresentazioni grafiche dei dati

Automazione del debugging: [[Debugging - Delta Debugging]]