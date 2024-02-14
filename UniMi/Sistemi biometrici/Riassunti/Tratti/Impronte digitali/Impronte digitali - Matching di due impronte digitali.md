Matching di due impronte digitali

Definizione del problema :
Supponiamo di avere un input due impronte digitali. Fare il matching tra queste due impronte significa rispondere alla domanda : "Le due impronte, provengono dalla stessa persona" ?

Abbiamo 4 possibili casistiche :
- Le impronte vengono dalla stessa persona e il sistema AFIS esegue un match corretto ( Correct Match)
- Le impronte vengono dalla stessa persona , tutta via il sistema AFIS dichiara il contrario ( False Non Match)
- Le impronte NON vengono dalla stessa persona e il sistema AFIS dichiara che esse provengono dalla stessa persona ( False match )
- Le impronte NON vengono dalla stessa persona e il sistema AFIS dichiara che esse NON vengono dalla stessa persona (Correct non Match)

Il problema del matching sulle impronte digitale è un problema molto complesso, questa complessità è dovuta alla grossa varianza tra i sample provenienti da uno stesso individuo ( grande intra-class variation).

Tale complessità si scontra con il pensione comune, il quale enuncia: 
Essendo le impronte la prima applicazione di sistemi automatici di pattern recognition, sia un problema completamente risolto. Al contrario ci sono numerose sfide che devono essere superare nel design di un sistema completamente automatico e affidabile di finger-print matchig, la prima tra tutte la bassa qualità dei sample. 


Difficoltà del problema
Esistono una vasta serie di fattori negativi,  ( qualità dell'immagine, pressione sul device, rumore del device, sudorazione della mano),  che influiscono sulla fase di acquisizione del sample, producendo diversi tipi di errori :
- Delle feature non esistenti nel tratto biometrico iniziale,  possono essere introdotte
- Delle feature genuine, ovvero pre-esistenti nel tratto biometrico, possono essere perse.

Tale feature aggiunte o eliminate sono causate da vari scenari :
- L'immagine di input (sample) potrebbe essere rumorosa o distorta ( polvere sul sensore, troppa pressione da parte dell'utente)
- L'utente potrebbe avere delle differenti condizioni della pelle in acquisizioni diverse.
- L'immagine di input potrebbe solo contenere una piccola porzione della impronta

Portando ai seguenti problemi :
- Non abbiamo un match esatto ( YES/NO), a differenza dei classici metodi di verifica basati su possesso e conoscenza.
- Il sample presentato in input al sistema, ( della persona che vi vuole accedere), potrebbe essere diverso dal templare della persona( memorizzato nel DB) , anche se rappresentano la stessa impronta digitale.

Contromisure che possiamo adottare per risolvere tali problematiche:
Come contromisure, è possibile creare un modello che appiattisce le differenze tra l'input e i template salvati su DB, in modo da ridurre gli effetti dei fattori negativi sugli algoritmi di matching.

Possiamo appiattire le differenze attraverso :
- Trasformazioni lineari, Rotazioni e traslazioni
- Deformazioni non lineari := Si tratta di andare a identificare una mappa delle deformazioni che l'impronta digitale ha subito, a causa della dimensione 2D( piatta) del sensore di acquisizione.

Questi algoritmi hanno il compito di ridurre la distanza intra-classe tra impronte digitali di uno stesso individuo. Tutta via hanno come lato negativo che vanno a diminuire anche la distanza inter-classe, alzando il tasso di false-matching.  (esame)


Come avviene il matching
Il matching tra due impronte consiste nel confrontare due sample di impronte ( o le loro features) dove, un sample sarà dato in input e l'altro sample sarà di riferimento ( salvato sul DB). Verrà calcolato  il loro livello di similarità,  la similarità tra due impronte viene espressa attraverso il matching score, tipicamente un valore tra 0 ( non simili) e 100 ( completamente identiche).

Alcune volte non si parla di similarità tra due impronte, ma di distanza tra due impronte.
Maggiore sarà la similarità delle due impronte, minore sarà  la distanza tra le loro caratteristiche. 

Possiamo formulare il problema del matching nel seguente modo :
una data coppia di insiemi di feature è considerata estratta dallo stesso individuo se il punteggio di match calcolato è maggiore di una soglia fissa.

Abbiamo diversi modi per realizzare il matching :
- Manuale
	- Un essere umano esperto di impronte digitali, usa una combinazione di immagine, caratteristiche dei ridge, ecc.. , per effettuare un matching
	- Questo tipo di "verifica" è ancora utilizzato nelle fasi finale dei sistemi automatici per aumentare l'accuratezza.
- Algoritmi basati su immagini ( correlation based)
	- Utilizza solamente una visione globale dell'impronta per il confronto, utilizzando i sample acquisiti ( immagini)
	- Richiede che vengano memorizzati interamente i sample ( dimensioni molto grandi)
	Tale approccio risolve alcune problematiche del modello minutae based, tutta via anch'esso presenta una serie di punti deboli :
	- Subisce gli effetti collaterali della traslazione e rotazione dei sample
- Minutae Based
	- Usa la posizione relativa dei minutae points
	- Se tratta dell'approccio più popolare per la verifica
	- Assomiglia all'approccio manuale, tutta via è automatico
	Come detto prima si tratta dell'approccio più usato nel mondo commerciale, tutta via presenta una serie di difficoltà :
	- Risulta difficile estrarre in modo automatico i punti minutae quando il sample ha una bassa qualità.
	- Non prende in considerazione il template globale dell'impronta e dei ridges.  Le strutture locali dei ridge non possono essere completamente classificate in questo approccio.

Un sistema di autenticazione commerciale basato sulle impronte digitali richiede un tasso di falso rifiuto (FAR) molto basso e un Falso tasso di accettazione (FAR) molto basso. Questo è molto difficile da ottenere con qualsiasi tecnica. L'uso di tecniche diverse può aumentare la precisione complessiva del sistema. In un'applicazione reale, il sensore, il sistema di acquisizione e la variazione delle prestazioni del sistema nel tempo è molto critica.


Image Based Matching : Optical Correletaion
Questa tecnica esegue semplicemente una correlazione tra due immagini. Il valore massimo della funzione di correlazione dipende se le due impronte provengono da un match genuino ( valori di correlazioni molti alti), oppure se provengono da un impostor match ( valori di correlazione bassi).

Vantaggi :
- L'immagine dell'impronta viene utilizzata come un template
- Permette di avere anche delle immagini a bassa risoluzione
- Matching molto veloce attraverso l'optical correlation.

Svantaggi :
- Il vantaggio di usare l'immagine come template si ripercuote sullo spazio di memorizzazione occupato dal template
- Richiede un accurato allineamento delle due impronte
- Non robusto a cambi di scala o a cambi nell'orientazione delle immagini.


Texture Based Matching FilterBanks
Questa tecnica estrae delle informazioni locali  da N regioni dell'immagine. Usando un banco di filtri Gabor di M filtri, estrae M coefficienti/immagini filtrate per ciascuna delle N regioni elaborate. L'algoritmo di matching compara N * M elementi fra le due immagini.

Vantaggi :
- Ha delle buone performance anche con delle impronte di scarsa qualità
- Usa delle informazioni riguardanti la texture dell'impronta per il matching ( non utilizzate negli algoritmi minutae o optical base)
- Le features sono statisticamente indipendenti dalla minutae e possono essere combinate con le minutae per avere un accuratezza più alta
- Le immagini possono essere normalizzate tramite delle tecniche molto semplici

Svantaggi :
- Richiede un ottimo allineamento delle impronte da confrontare
- Può essere soggetto agli effetti collaterali causati dalle rotazioni e traslazioni
- Meno accurato degli algoritmi minutae based

Minutae based Matching
Minutae base tecniche, per prima cosa vanno a trovare le coordinate dei minutae points  ( biforcazioni e terminazioni dei ridge) nelle due impronte, permettendo così di comparale. Per effettuare una corretta comparazione dei minutiae points occore eseguire le seguenti operazioni preliminari :
- Allineamento delle rotazioni
- Allineamento della scala
- Allineamento delle traslazioni
- Riduzione della distorsione elastica
![[Pasted image 20231106105555.png]]

Il problema del matching delle impronte è sostanzialmente un problema di point pattern matching.
Verranno dunque comparati due set di punti ( minutae), un set proveniente dal sample della impronta in input, l'altro set dal template presente sul db.

I punti minutiae possono essere rappresentati in una matrice :
$M = (m_1, m_2, ..., m_n)^T$

Dove ogni $m_i$, è il seguente set di valori
$m_i = (X, Y, \phi, T_i)$
- X e T sono le coordinate dell'i-esimo punto minutae
- $\phi$ è l'angolo di orientamento
-  T è invece il tipo di minutiae ( biforcazione o terminazione di un ridge)

Vantaggi di questa tecnica :
- Invariante alle traslazioni, rotazioni e cambiamento di scala dell'immagine
- Molto accurato

Svantaggi di questa tecnica :
- L'estrazione delle minutiae richiede dei sample ad alta qualità
- Non robusto alle trasformazioni non -lineari ( deformazioni)
- Non utilizza informazioni riguardante l'analisi globale dell'impronta ( texture, ecc..)


Core based approccio
I punti core rilevati in un impronta vengono utilizzati per allineare due immagini.
La maggior parte degli algoritmi non core base, consumano molto tempo di elaborazione, di conseguenza i core based risultano più efficenti.

Approccio Local Structure
Vantaggi :
- Sono invarianti alle rotazioni e traslazioni, in quanto considerano solamente le differenze di direzione e locazione delle minutiae.

Svantaggi
- Questo approccio può tollerare solamente delle basse deformazioni, siccome processano delle analisi solo su piccole porzioni dell'immagine.
- Possiamo avere solamente poche strutture ( minutae) da confrontare, inoltre potremmo avere molte minutae "create" irroneamente e poche minutae genuine.


Aproccio globale :
Vantaggi :
- Determinazione affidabile dell'unicità delle impronte digitali.

Svantaggi :
- È necessario un pre-processare il sample in input prima di utilizzarlo per il matching
- Le feature globali sono dipendenti dalla rotazione e traslazione dell'impronta digitale.
- Performace basse

Aproccio ibrido :
Questo approccio fa uso di caratteristiche sia locali che globali prese dalle immagini FP.
- Innanzitutto, vengono utilizzate le funzionalità locali per individuare la "coppia di minuzie con la migliore corrispondenza", una nell'input FP e l'altra nel modello FP.
- In secondo luogo, la migliore struttura locala abbinata fornisce le corrispondenze per allineare i due FP.
- Infine, il "livello di somiglianza" è calcolato e confrontato con la soglia per decidere il risultato di corrispondenza.

Altri approcci ibridi controllano se due regioni di un'impronta digitale sono simili controllando se i triangoli in mezzo sono simili. Successivamente si controllano gli angoli, le distanze misurate ( utilizzando i numeri di cresta) e i tipi di minuzie.


State of the ART
Occupiamoci ora di analizzare le performance di alcuni sistemi che effettuano il matching delle impronte. Esistono principalmente due archivi di impronte, il primo è messo a disposizione dal (NIST USA), il secondo è messo a disposizione da un organizzazione globale ( FCV2004).
- Il DB del NIST, contiene solamente delle impronte rilevate tramite metodi off-Scan ( inchiostro, ecc..).
- Il DB FCV2004, contiene solamente immagini di impronte acquisite tramite appositi sensori.
Inoltre si tratta di un sistema di valutazione automatico online per gli algoritmi di riconoscimento  delle impronte digitali. I test vengono eseguiti su sequenze di opportuni data set e i risultati vengono pubblicati online.

Per quanto riguarda la velocità di matching, il record mondiale è detenuto da una Compagnia tedesca DERMALOG, la quale riesce a comparare 3.6 bilioni di impronte al secondo, trovano dei possibili matching con una certa soglia di accuratezza.
È bene notare come  la velocità di matching senza l'accuratezza  abbastanza inutile.