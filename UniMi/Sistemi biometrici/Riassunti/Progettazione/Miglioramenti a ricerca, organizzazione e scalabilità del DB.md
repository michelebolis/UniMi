L'obbiettivo principale è quello di migliorare la scalabilità. Dobbiamo garantire che i sistemi che devono gestire una grande quantità di identità, dovrebbero essere in grado di `operare efficacemente quando il numero di utenti registrati nel DB aumenta`.

Si richiede inoltre che il `tasso di peggioramento delle prestazioni sia minore del tasso dei nuovi utenti immessi nel sistema`.

L'introduzione della biometria in un sistema di identificazione di grandi dimensione porta ad una serie di vantaggi:
- Le tecnologie biometriche non soffrono come quelle tradizionali del problema della produzione e del rinnovo dei documenti di identità.
	- Rinnovo della care di identità del passaporto per scadenza o smarrimento
- Le tecnologie biometriche iniziano ad essere competitive in termini di costo e mantenimento.
	- Un buon lettore biometrico funziona per anni, non ha bisogno di particolari aggiornamenti tecnologici.

L'obiettivo di gestire efficacemente la complessità delle ricerche all'incremento del numero di template nel DB del sistema può essere raggiunto solo con una `attenta organizzazione del DB`, un DB organizzato permette di `non confrontare un template in ingresso con tutti i template nel DB ma solo con quelli contenuti in una partizione`.

Ad esempio :
Le impronte possono essere classificare come "arch", "loop" ecc.. Se il sistema usa due impronte, allora i matching verranno effettuati solo con la porzione di database contenente template di individui con le due impronte dello stesso tipo di quelle in ingresso.

Ad esempio per un sistema basato su due impronte e capace di calssificarle in arch o loop avremmo 4 partizioni o bin possibili. 

![[Pasted image 20231106095131.png]]

Attualmente i sistemi di grandi dimensione funzionanti su due impronte riescono a funzionare correttamente con dei Penetration Rate del 10%.

Per giovare delle partizioni del DB occorre `disporre di un algoritmo automatico molto robusto per la classificazione dei template`. Quando il DB viene creato, i template vengono disposti nelle partizioni (bins)

Il `numero di bins può essere calcolato` nel seguente modo :
Se ho N impronte disponibili (indice, medio, …) tutte divisibili in $N_{tipi}$ ( arch,loop,…) allora il numero migliore di bin è dato da: $N_{bin} = N_{tipo}^{NumeroImpronte}$ 
Ad esempio:
Se abbiamo due impronte ( N impronte = 2 )
Con 3 tipi possibili in cui un impronta viene classificata ( $N_{tipi} = 3$ )
Il numero di bins ottimale è $N_{bin} = 3^2 = 9$

`Binding error`:
I problemi nascono quando `un individuo presenta i propri tratti biometrici al sistema e l'algoritmo di classificazione del tratto sbaglia il bin` ( binding error).
Se l'individuo era registrato nel DB, con alta probabilità non si avrà un match in quanto i template che matchano sono registrati da un bin diverso da quello scandito.

`Penetration rate`: percentuale (spesso espressa con un rapporto) con cui un sistema è `in grado di identificare correttamente gli utenti all'interno del DB`.
`La frazione media di template che occorre controllare nel DB per tutti i possibili input, tenendo conto che la ricerca continui nella partizione anche se si verifica un match`.
Tiene conto della distribuzione degli individui.

(esame) _N:B =  Avere N bin non porta ad avere un penetration rate del 100/N_. Questo accade perché i bin non contengono necessariamente un numero di individui uguali.  `La distribuzione degli individui nei bin dipende dalla distribuzione statistica della popolazione che quasi mai è uniforme`.

È dimostrato come si possa arrivare ad un `tasso di errore del 5-10% in un db di medie dimensioni` attuando una classificazione di Henry con un sistema automatico ( 5 classi). Gli errori si moltiplicano se si usano N impronte.

Notare cosa succede abbassando il numero di classi :
- `P.R. sale, si abbassa la qualità del P.R. ottenibile` (non buono)
- `Si abbassa l’errore di classificazione` (buono)

Domande esame:
- Scalabilità ed organizzazione della ricerca in un DB biometrico
- Il sistema di partizione (binning) del DB mediante classificazione del tratto biometrico
- Le differenze fra il Penetration Rate ed il Binning rate