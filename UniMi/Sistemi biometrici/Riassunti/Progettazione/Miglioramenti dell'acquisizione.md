Miglioramenti dell'acquisizione
Il modulo di acquisizione è critico, se nel sistema entra un tratto di scarsa qualità otterremo un risultato con un accuratezza di bassa qualità. Potrebbe far cadere l'accuratezza della catena dell'intero sistema biometrico ( esame)

Il processo di acquisizione si suddivide in due fasi :
- Valutazione della qualità ( quality assesment) := controllo automatico sulla correttezza dei dati in ingresso.
- Segmentazione ;= Separazione dei dati in ingresso tra quelli effettivamente utili per rilevare dei template ( foreground) e i cosi detti dati di background, informazioni non rilevanti.

È buona prassi cercare di estrare maggiori informazioni possibili per migliorare le performance del sitema biometrico, di conseguenza :
- Viene acquisito anche il contesto attorno al sample :
	Ad esempio potrebbe essere acquisito lo sfondo per meglio segmentare il volto.
- Evitare sul nascere di effettuare cattive acquisizioni :
	Per non dover richiedere il sample, ad esempio potrebbe essere controllato se il soggetto è in movimento prima di acquisire il volto che potrebbe risultare fuori fuoco. Vengono presi tanti frame e viene scelto il migliore.

Ovviamente posso aumentare il numero di informazioni trasmesse per migliorare la fase di acquisizione se ho abbastanza potenza computazionale.

Esempio basato sull'impronta
Di solito il sample di un impronta è ottenuto dalla proezione bidimensionale dell'impronta su una superficie piatta.
L'impronta viene quindi posta sul sensore applicando una pressione adeguata.

Alcuni miglioramenti potrebbero essere :
- Acquisire un immagine 3d dell'impronta
- Acquisire una immagine a colori ( anche per evitare eventuali frodi)
- Usare sistemi di active sensing: indica sensori avanzati, automaticamente addanti alla caratteristiche ambientali.

Acquisizione : controllo della qualità
Dopo l'acquisizione molto sistemi attuano un controllo automatico della qualità del tratto, esso permette di prevenire problemi di matching i quali possono abbassare l'accuratezza del sensore.

I sistemi di controllo della qualità producono un indice di qualità del sample acquisiti. Tutta via tale sistema è difficile da creare in quanto non esiste una definizione matematica di qualità.

Punti critici per la realizzazione :
- Non sempre esiste un modello rigoroso e realistico della misura in ingresso da usare per calcolare l'indice.  Ad esempio, se potessimo definire come dovrebbe essere fatta una immagine ottimale di un impronta potremmo esprimete l'indice di qualità come la "distanza" dell'immagine in ingresso da quella ottima.
- Non sempre esistono metriche rigorose e robuste per misurare la distanza del sample in ingresso con il riferimento ottimale.

Di conseguenza seguiamo tra approcci :
- Globali := bassati su metriche globali ( contrasto del grigio)
- Locali
- Con calssificatori  = modello di reti neurali
- Misti

Enanchement :
Non è sempre possibile rifiutate un sample di bassa qualità, in alcuni casi è l'unico sample disponibile.
Il sistema in questo caso dovrà cercare di estrarre le informazioni foreground dal rumore background, in modo tale da far funzionare il resto della catena di moduli del sistema :
- Questa fase prende il nome di signal/immage enhancement
- Solitamente è ad elevata complessità computazionale
- Può generare artefatti. Se esagero nel filtraggio dei dati possono andare a creare delle minuzie che non erano presenti nel sample originale.

Domande esame:
- variabilità temporale, intraclasse ed interclasse
- acquisizione delle informazioni del sistema biometrico
- misura della qualità del tratto biometrico
- miglioramento della qualità dei segnali/immagini e l’introduzione degli artefatti 
- segmentazione