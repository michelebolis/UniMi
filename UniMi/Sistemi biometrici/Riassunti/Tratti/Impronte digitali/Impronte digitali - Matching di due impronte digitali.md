Definizione del problema :
Supponiamo di avere un input due impronte digitali. Fare il matching tra queste due impronte significa rispondere alla domanda : "Le due impronte, provengono dalla stessa persona" ?

Abbiamo 4 possibili casistiche:
- Le impronte vengono dalla stessa persona e il sistema AFIS esegue un match corretto ( Correct Match)
- Le impronte vengono dalla stessa persona , tutta via il sistema AFIS dichiara il contrario ( False Non Match)
- Le impronte NON vengono dalla stessa persona e il sistema AFIS dichiara che esse provengono dalla stessa persona ( False match )
- Le impronte NON vengono dalla stessa persona e il sistema AFIS dichiara che esse NON vengono dalla stessa persona (Correct non Match)

Il problema del `matching sulle impronte digitale è un problema molto complesso`, questa complessità è dovuta alla `grossa varianza tra i sample provenienti da uno stesso individuo` (grande `intra-class variation`).

Tale complessità si scontra con il pensione comune, il quale enuncia: 
Essendo le impronte la prima applicazione di sistemi automatici di pattern recognition, sia un problema completamente risolto. Al contrario ci sono numerose sfide che devono essere superare nel design di un sistema completamente automatico e affidabile di finger-print matchig, la prima tra tutte la bassa qualità dei sample. 


Difficoltà del problema
Esistono una `vasta serie di fattori negativi`,  (qualità dell'immagine, pressione sul device, rumore del device, sudorazione della mano), che influiscono sulla fase di acquisizione del sample, producendo diversi tipi di errori:
- Delle `feature non esistenti` nel tratto biometrico iniziale, possono essere `introdotte`
- Delle `feature genuine`, ovvero pre-esistenti nel tratto biometrico, possono essere `perse`.

Tale feature aggiunte o eliminate sono causate da vari scenari :
- L'`immagine` di input (sample) potrebbe essere `rumorosa o distorta` (polvere sul sensore, troppa pressione da parte dell'utente)
- L'utente potrebbe avere delle `differenti condizioni della pelle` in acquisizioni diverse.
- L'immagine di input potrebbe solo contenere una piccola porzione della impronta

Portando ai seguenti problemi :
- `Non abbiamo un match esatto` (YES/NO), a differenza dei classici metodi di verifica basati su possesso e conoscenza.
- Il sample presentato in `input` al sistema, (della persona che vi vuole accedere), potrebbe essere `diverso dal template della persona` (memorizzato nel DB), anche se rappresentano la stessa impronta digitale.

`Contromisure` che possiamo adottare per risolvere tali problematiche:
Creare un `modello che appiattisce le differenze tra l'input e i template salvati` su DB, in modo da ridurre gli effetti dei fattori negativi sugli algoritmi di matching.

Possiamo appiattire le differenze attraverso :
- `Trasformazioni lineari, Rotazioni e traslazioni`
- `Deformazioni non lineari`: si tratta di andare a identificare una mappa delle deformazioni che l'impronta digitale ha subito, a causa della dimensione 2D( piatta) del sensore di acquisizione.

Questi algoritmi hanno il compito di `ridurre la distanza intra-classe` tra impronte digitali di uno stesso individuo. Tutta via hanno come lato negativo che vanno a diminuire anche la distanza inter-classe, alzando il tasso di false-matching. (esame)


Come avviene il matching
Il matching tra due impronte consiste nel `confrontare due sample di impronte` (o le loro features) dove, `un sample sarà dato in input e l'altro sample sarà di riferimento` ( salvato sul DB). 
Verrà calcolato il loro `livello di similarità`, la similarità tra due impronte viene espressa attraverso il `matching score`, tipicamente un valore tra 0 (non simili) e 100 (completamente identiche).

Alcune volte non si parla di similarità tra due impronte, ma di distanza tra due impronte.
`Maggiore sarà la similarità delle due impronte, minore sarà la distanza tra le loro caratteristiche`. 

Possiamo formulare il problema del matching nel seguente modo :
una data coppia di insiemi di feature è considerata estratta dallo stesso individuo se il punteggio di match calcolato è maggiore di una soglia fissa.

Abbiamo diversi modi per realizzare il matching:
- `Manuale`
	- Un `essere umano` esperto di impronte digitali, usa una combinazione di immagine, caratteristiche dei ridge, ecc.. , per effettuare un matching
	- Questo tipo di "verifica" è ancora utilizzato nelle fasi finale dei sistemi automatici per aumentare l'accuratezza.
- `Algoritmi basati su immagini` (Correlation based)
	- Utilizza solamente una `visione globale` dell'impronta per il confronto, utilizzando i sample acquisiti ( immagini)
	- Richiede che vengano memorizzati interamente i sample ( dimensioni molto grandi)
	Tale approccio risolve alcune problematiche del modello minutae based, tutta via anch'esso presenta una serie di punti deboli:
	- `Subisce gli effetti collaterali della traslazione e rotazione dei sample`
	- [[Image Based Matching]]
	- [[Texture Based Matching FilterBanks]]
- `Minutae Based`
	- Usa la `posizione relativa dei minutae points`
	- Assomiglia all'approccio manuale, tuttavia è `automatico`
	Come detto prima si tratta dell'approccio più usato nel mondo commerciale, tutta via presenta una serie di difficoltà:
	- `Risulta difficile estrarre in modo automatico i punti minutae quando il sample ha una bassa qualità`.
	- Non prende in considerazione il template globale dell'impronta e dei ridges.  Le `strutture locali dei ridge non possono essere completamente classificate in questo approccio`.
	- [[Minutae based Matching]]

Un sistema di autenticazione commerciale basato sulle impronte digitali richiede un tasso di falso rifiuto (FAR) molto basso e un Falso tasso di accettazione (FAR) molto basso. Questo è molto difficile da ottenere con qualsiasi tecnica. L'`uso di tecniche diverse può aumentare la precisione complessiva del sistema`. In un'applicazione reale, il sensore, il sistema di acquisizione e la variazione delle prestazioni del sistema nel tempo è molto critica.


Core based matching
I `punti core` rilevati in un impronta vengono utilizzati `per allineare due immagini`.
La maggior parte degli algoritmi non core base, consumano molto tempo di elaborazione, di conseguenza i `core based risultano più efficienti`.

Approccio Local Structure
Vantaggi: sono `invarianti alle rotazioni e traslazioni`, in quanto` considerano solamente le differenze di direzione e locazione delle minutiae`.
Svantaggi
- Questo approccio `può tollerare solamente delle basse deformazioni`, siccome processano delle analisi solo su piccole porzioni dell'immagine.
- Possiamo avere solamente `poche strutture (minutae) da confrontare`, inoltre potremmo avere molte minutae "create" irroneamente e poche minutae genuine.


Approccio globale:
Vantaggi: determinazione affidabile dell'unicità delle impronte digitali.
Svantaggi:
- È necessario un `pre-processare il sample in input prima di utilizzarlo per il matching`
- Le feature globali sono `dipendenti dalla rotazione e traslazione` dell'impronta digitale.
- Performace basse

Approccio ibrido:
Questo approccio fa uso di caratteristiche sia locali che globali prese dalle immagini FP.
- Innanzitutto, vengono `utilizzate le funzionalità locali per individuare la "coppia di minuzie con la migliore corrispondenza"`, una nell'input FP e l'altra nel modello FP.
- In secondo luogo, la `migliore struttura locale abbinata fornisce le corrispondenze per allineare i due FP`.
- Infine, il `"livello di somiglianza" è calcolato e confrontato con la soglia per decidere il risultato di corrispondenza`.

Altri approcci ibridi controllano se due regioni di un'impronta digitale sono simili controllando se i triangoli in mezzo sono simili. Successivamente si controllano gli angoli, le distanze misurate ( utilizzando i numeri di cresta) e i tipi di minuzie.


State of the ART
Esistono principalmente `due archivi di impronte`, il primo è messo a disposizione dal (NIST USA), il secondo è messo a disposizione da un organizzazione globale (FCV2004).
- Il DB del NIST, contiene solamente delle impronte rilevate tramite metodi off-Scan ( inchiostro, ecc..).
- Il DB FCV2004, contiene solamente immagini di impronte acquisite tramite appositi sensori.
Inoltre si tratta di un sistema di valutazione automatico online per gli algoritmi di riconoscimento  delle impronte digitali. I test vengono eseguiti su sequenze di opportuni data set e i risultati vengono pubblicati online.

Per quanto riguarda la velocità di matching, il record mondiale è detenuto da una Compagnia tedesca DERMALOG, la quale riesce a comparare 3.6 bilioni di impronte al secondo, trovano dei possibili matching con una certa soglia di accuratezza.
È bene notare come  la velocità di matching senza l'accuratezza  abbastanza inutile.