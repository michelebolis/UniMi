Possibili valutazioni di un sistema biometrico :
Un sistema biometrico può essere valutato sotto diversi aspetti :
- Technology evaluations  : = Si tratta di valutazione offline, vengono effettuate utilizzando più algoritmi per la stessa modalità biometrica.
- Scenario evaluations := Valutazioni in cui le prestazioni del sistema sono valutate in un prototipo o in un applicazione simulata.
- Operational evaluations := Valutazione un cui l'intera valutazione del sistema biometrico viene determinata in un specifico ambiente applicativo, con un specifico target di utenti.

Ogni valutazione ha le sue regole da seguire ed i suoi parametri da misurare.

Tecnology Evaluation
- Servono per eseguire prove in "laboratorio" con algoritmi e database di sample standard.
- Sono il primo passo di applicazione di un algoritmo generico vero un tipo di applicazione più specifica :
	- Per ottenre i dati vengono utilizzati una serie di sensori sia fisici che virtuali
	- Sono stati scelti degli utenti di una particolare operazioni.
- Prevedono un rilascio di parte di dati per effettuare il tuning degli algoritmi. Successivamente gli algoritmi vengono testati su dei dataset a loro sconosciuti.
	Il data set segreto viene utilizzato anche per il confronto degli algoritmi.
- Conviene utilizzare queste valutazioni durane le fasi di sviluppo di algoritmi/sistemi.

Scenario evaluation
- I test controllano un sistema biometrico completo in condizioni che simulano l'applicazione sul campo.
- Di solito vengono testate diverse combinazioni di algoritmi e sensori. L'obbiettivo è trovare la combinazione che offre performance migliori per creare il sistema finale da implementare.
- In questa fase di valutazione, la popolazione è chiusa e limitata, quandi la veridicità statistica dei dati può risultare compromessa.

Operational Evaluations
- Simile alla prova in condizioni di "scenario" ma eseguita :
	- Su una specifica applicazione
	- Con uno specifico algoritmo
	- Sul posto esatto dell'applicazione
	- Si impiegano gli utenti finale dell'applicazione
- Si ottengono risultati vicini a quelli che compariranno nell'applicazione finale.
- I test di questo tipo non sono facilmente ripetibili . Non è possibile ricreare esattamente le stesse condizioni in altri esperimenti di verifica.

Online Evaluation vs Offline evaluation :
- ONLINE =  Si tratta di tipi di sistemi che pretendono di eseguire l'enrolment o il matching al momento dell'acquisizione del sample da parte del sensore.
	- Il vantaggio principale è che il sample può essere immediatamente scartato. Tutta via è consigliabile che l'immagine o il segnale siano collezionabili.
	Con valutazioni su scenari e test operativi, le transazioni online potrebbe essere più semplici per il tester (il sistema funziona al suo solito modo) e, anche se consigliato, l'archiviazione di immagini o segnali non è assolutamente necessario
- OFFLINE = l'esecuzione dell'enrollment o del matching avviene in un momento separato rispetto all'acquisizione dell'immagine da parte del sensore :
	- Vengono collezionate una serie di immagini per l'enrollment offline e il matching offline. Questa caratteristica permette di avere un gran controllo su quali tentativi e template devono essere utilizzati in ogni transizione
	
	Ad esempio è possibile sistemare il quality check module
	
	- I test di tipo tecnologico portano a salvarsi i sample in ingresso per delle computazioni offline.

N.B = i tassi di errore non significano nulla se non è possibile associarli un tasso di confidenza ad ogni misura. Gli intervalli di confidenza vengono costruiti di solito non da esperimenti, ma da un modello statistico che deve descrivere meglio possibile l'esperimento.


Comparazione dei sistemi
La comparazione dei sistemi biometrici, avviene comparando i valori degli indici di merito viste nelle lezioni precedenti :
- Numeri puri come EER, FTM; FNTM; FAR. Meglio se espresse rispetto alla soglia T del sistema biometrico.
- Descrittive :
	- Distribuzione dei genuini pn(t)
	- Distribuzione degli impostori pm(t)
- La comparazione maggiormente efficace è quella che si può avere confrontando le curve DET ( o ROC ) dei due sitemi in merito.

MEMO SU ROC
ROC = 1 - DET
La curva ROC e la curva DET mostrano la stessa informazione ma si focalizzano su punti di vista differenti. Riferendosi ad autenticazione positiva :
- La curva DET mostra quanti genuini non passano FNMR
- La curva ROC mette in mostra quanti genuini passano

Comparazione con DET  :
Non sempre la comparazione basato su EER è adatta. Bisogna scegliere la regione di funzionamento del sistema in termini di FNMR e FMR e successivamente confrontare i sistemi in quelle due zone della curva, per vedere quale sistema si comporta meglio.

Deve essere richiesto al commitente un grado di FNMR e FMR, nel quale l'applicazione deve lavorare.

Errore zero sempre impossibile nella pratica

![[Pasted image 20240214093256.png]]

Comparazione con CMC

La curva rappresenta la probabilità di identificare una persona in base al pool di impronte che abbiamo selezionato. Le impronte nel pool sono ordinate in base al match score.

Si usano solo gli score, non si usa nessuna soglia.

![[Pasted image 20240214093309.png]]


La curva CMC non è derivabile da altri plot

Distribuzioni molto ben separate ( fra genuini e impostori) produrranno poi una buona curva DET e ROC e CMC.

Buona ROC non è detto buona CMC

![[Pasted image 20240214093319.png]]

Diverse CMC possono avere la stessa ROC

Sistemi biometrici diversi ( stessi sample = tecnology evaluation ) con diverse CMC possono avere la stessa DET/ROC.  Perché

- Sheep : basso FMR, basso FNMR
- Goats  alto FNMR
- Lambs alto FMR
- Wolf alto FMR

La distribuzione individuale dice se mi comporto bene verso me stesso e verso gli altri.

Ogni identità contribuisce in maniera unica alle performace del sistema, ovvero le statistiche aggregate DET/ROC non predicono bene le statistiche rank che dipendono esattamente dagli individui.


Comparazione con distributori genuini e impostori:
Le distribuzione dei match score sono alla base delle curve ROC, CMC, DET.
Sono un ottimo modo per vedere il comportamento del sistema e capire se ci sono :
- Assimetrie
- Code non simmetriche
- outlier

Distribuzioni d'
D' è la misura del grado di separazione presente fra le distribuzioni degli impostori e dei genuini, calcolato considerando le loro medie e deviazioni standard .

Il parametro d' da solo non è esaustivo , stesso d' ma DET diverse.


Indici aggiuntivi :
Possiamo descrivere le regioni di una curva DET nel seguente modo :
Regioni con bassi FMR -> regioni di security  1-FAR(t):
- Bassa possibilità che un utente non autorizzato possa entrare nel sistema.
- Tutta via la probabilità che un utente autorizzato non riesca ad entrare nel sistema al primo tentativo è più alta. Occorrerà che l'utente presenti più volte il suo tratto biometrico al sensore.
Regioni con baso FNMR -> regioni di convenience 1-FRR(t) :
- Un utente autorizzato non perde tempo, in quanto con bassa probabilità non entrerà al primo tentativo
- Tutta via avremo una percentuale più alta di utenti non autorizzati che riescono ad accedere al sistema.