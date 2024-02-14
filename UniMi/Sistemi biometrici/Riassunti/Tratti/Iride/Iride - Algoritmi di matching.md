Iride - Algoritmi di matching
Ma che correlazione c'è tra i bit che compongono un IRIS CODE :
La probabilità che un bit all'interno dell' IRIS CODE sia zero oppure uno è del 50%, significa che l'iris code è (quasi) un codice a massima entropia. 

Questo significa che sono presenti delle correlazioni fra i bit all'interno dell'iris code, in quanto la struttura è auto-predittiva .

Queste correlazioni fra bit tutta via, limitano i veri gradi di libertà di un irisCode :
- In altre parole non è vero che l'IRIS code nasce come un numero binario del tutto casuale.
- Alcuni gruppi di bit portano ad incontrare nell'iris code una maggiore probabilità  di incontrare atri gruppi di bit.

Alcuni fattori che aumentano la variabilità intraclasse :
- Rotazioni della testa
- Variazioni dello zoom nelle ottiche
- Dilatazione della pupilla

Algoritmi di matching per gli irisCode :
La comparazione è effettuata fra IRIS CODE di 256 byte attraverso il calcolo della distanza di hamming :
La distanza di hamming (HD) fra due stringhe A e B è il numero di bit in disaccordo fra le due stringhe, normalizzati al numero totale di N bit.
Normalmente N = 2048 bit, se non vi sono occlusioni dell'iride

Se vi sono occlusioni dell'iride, riflessi, ciglia, occorre preparare delle maschere di oscuramento delle zone dove non vi è un informazione utile. Andremo a togliere dal calcolo della distanza di hamming le zone dove non vi è informazione utile.

Velocità del matching :
L'esecuzione degli And e degli Xor può avvenire a blocchi di bit pari alla lunghezza di parola del processore ( tipicamente almeno 32 bit).

Questo rende il matching estremamente veloce. È possibile parallelizzare la ricerca anche su DB di grosse dimensioni.

Esempio :
- Su un processore 300 Mhz, si riescono ad eseguire ad eseguire 100.000 comparazioni al secondo
- Su un server a 3Ghz si arriva ad 1 milione di Irscode comparati in un secondo
- Server dedicati con software proprietari citano 25 milioni di occhi al secondo. NEC dichiara 230 Milioni match al secondo.

Distribuzioni dell'IRIS CODE
- In teoria, due irisCode calcolati dall'iride della stessa persona dovrebbero avere distanza di Hamming = 0.
- Nella realtà fra due acquisizioni perfettamente eseguite a pochi istanti una dall'altra si può osservare uno spostamento di +- 1 posizioni del pattern  nei due template ( scarto di +- 2 bit)

Per i seguenti motivi, vengono eseguite 3 comparazioni e si sceglie il minimo valore di distanza di hamming nelle 3 comparazioni, come valore finale.
![[Pasted image 20231115093538.png]]
Miglior fitting della distribuzione della distanza di hamming degli impostori con iriscode da 20148 bit con 7 shift.

Se la soglia t viene abbassata di poco sotto a 0,3 la probabilità di avere un impostore distante da me di Hd bit diventa irrisoria.

Si tratta di distribuzioni ideali per un sistema biometrico, in quanto le distribuzioni sono perfettamente separabili.

---

Tassi di errore del sistema :
- In lettura sono presenti studi sia teorici sia applicativi che dimostrano che i tassi di errori siano nulli FMR = 0.
- Altri studi indicano FTE = 7%
- FNMR in verifica = 6 %   FNMR identificazione su 1,4 milioni di individui < 0.001

Come varia il tasso di errori al variare del numero di tentativi :
- Al primo tentativo di verifica dell'identità in un sistema di riconoscimento dell'iride, avremo un FTE del 7% al primo tentativo. (FNMR = 4% FMR = 0 )
- Dopo 3 tentativi non cambia assolutamente nulla, avremo sempre un FMR pari a 0, ma avremo un miglioramento del FNMR = 0,4 %

Ad oggi, probabilmente esite solo la stima "ufficiale" di quanto sia l'accuratezza dell'iride aggiornata al 2018 :
Ad oggi,  l'attuale record  è di un tasso di errore nella identificazione dello 0,5 % ( con 12 milioni di persone), mentre un accuratezza del matching di circa 99.33%.
- le stime viste in tabella sono OTTIMISTICHE e la vera probabilità di False Match in realtà dipende dalla qualità delle ottiche! Occorre procedere ad un test sul campo sempre!
- In ogni caso, ad oggi, i sistemi basati su Iriscode sono i sistemi biometrici “livescan” più accurati esistenti

Numero di bit significativi nell' IRIS code :
Gli iris code mediamente distano un numero di bit come delle stringhe casuali di 249 bit.
Fissiamo una certa soglia, la probabilità che due persone abbiano in comune il 31 % di 249 bit casuali è infinitesima. La soglia è perfettamente aderente ad un binomiale con 249 gradi di libertà e p = 0.5. 

Il  numero di bit significatici nell'iris code dipende dalla condizioni operative :
- Il tipo di distribuzione degli impostori ottenuta usano l'iris Code non cambia di solito
- Cambiano i parametri sulla curva, ovvero cambia il numero di bit significativi, rimangono comunque molti.

Se riusciamo a stimare la distanza di hamming fra IRIS code di diversi impostori, possiamo calcolare quanti tentativi dovremmo fare per trovare il primo false match( ovvero un impostore che entra). Il numero di tentativi è infinitesimo e cresce all'aumentare della distanza di Hamming soglia per considerare un match positivo o meno.

La soglia della distanza di hamming che meglio divide le distribuzioni può essere calcolata come segue :
- Adattamento del criterio  in base alla dimensione N del DB, per evitare accumulazione delle probabilità di false match.
- Ri-normalizzazione della distanza di hamming quando solo n bit  dell'IRiS code sono disponibili a causa delle occlusioni


Distribuzioni di occhi geneticamente uguali :
Partendo dal presupposto che nel DNA non ci siano dei geni per l'occhio destro e quello sinistro, possiamo supporre che l'occhio Destro e quello Sinistro nascano dagli stessi geni.

Sono gli occhi più vicini fra loro che possiamo trovare in natura, ma quandi qual è la loro distanza di hamming ?

Sono stati confrontati fra loro le due iridi di 324 persone, ottenendo una distribuzione del tutto uguale a quella dei confronti fra persone diverse.

Questo significa che , a parte il colore degli occhi Dx E SX sono diversi tanto quanto quelli di persone diverse per L'IRIS CODE .


Tecniche di spoofing per iride
Se i problemi delle carte di credito rubate e delle frodi legate al furto di identità sembrano poter essere risolte efficacemente con le impronte digitali, l’iride si presta meglio ad applicazioni con livelli di sicurezza e dimensioni maggiori

In particolare, il bassissimo tasso di FMR (“dire che tu sei un altro”) dei sistemi basati sull’iride rende la tecnica perfetta per la scansione di enormi DB anche a livello nazionale

Attualmente l’iride è l’unico sistema che offre la scansione realtime di una singola iride (pochi secondi) con un DB di milioni di iridi, o di una watch list centralizzata

Tutta via con questo sistema abbiamo e avremo dei grossi problemi di privacy :

L’exploit di Daugman (riconoscimento con iride da foto ad alta risoluzione nel visibile a 18 anni di distanza) mostra la possibilità del pericolo di screenig di massa dagli archivi di foto (governativi, social, …). Questo fenomeno inoltre è in continua evoluzione grazie a i seguenti fattori :
- Miglioramento delle tecniche di segmentazione estrazione iriscode
- Foto a ottiche dedicate sempre di maggiore risoluzione e perfetto fuoco sul volto ( selfie)
- Capacità delle tecniche di iris code di avere un FMR quasi nullo.

Le frodi attuabili sul sistema sono molte e possono essere le seguenti :
- Attaccare i canali di comunicazione del sistema ( replay attacks) specialmente il canale di comunicazione dal sensore al sistema.
- Attaccare dei moduli specifici.
- Attaccare il DB con tutti i dati di enrollment
- Ingannare il sensore, di solito presentando un iride finta

Attacchi al sensore :
Un attacco piuttosto semplice può consistere nel proporre una fotografia, alcuni sistemi basati sull'iride non hanno alcun tipo di test di liveness ( possono essere ingannati).

Una iride falsificata mediante una lente a contatto stampata presenta molte delle caratteristiche di liveness ( spostamenti pupilla di dimensioni variabili, materiale biologico ). Il processo di stampa della lente porta una periodicità nella trama della stampa che si rileva nello spetto 2d del segnale.

Generazione sintetica di iridi :
Sono disponibili tecniche per la generazione sintetica di iridi mediante algoritmi basati su "Markov random Fields". Iterativi.
Sono tecniche di generazione sintetica di pattern  :
- Si parte da piccole porzioni di immagine reale ( primitive)
- Si crea una matrice casuale
- Le primitive vengono mischiate casualmente agendo su un indipendent random field in modo iterativo.

Sono disponibili anche tecniche multistrato :
- Si prepara un modello 3d dell'iride
- Si preparano con vari algoritmi gli strati con delle tipologie di texture orientate in modo pseudo casuale.
- Si sovrappongono gli strati tenendo contro delle trasparenze
- Si adatta l'immagine degli strati al modello 3d e si calcolano le luci e el ombre

In entrambi casi sono possibili dei nuovi sviluppi attraverso l'utilizzo delle CNN ( convilutional neural network). Tale tecnologia inoltre permette la creazione di iridi 3D.

Possibili controlli :
- La pupilla reagisce alle variazioni di luce ambientali, un occhio finto no. Inoltre la velocità di contrazione e dilatazione sono diverse ed hanno un andamento prefissato.
- Sprettrometria e termografia :
Usando illuminatori a frequenze ottiche diverse è possibile avere in tempo reale una spretografia dell'iride.

Attraverso dei sistemi di classificazione che analizzano lo spettogramma dell'iride si stima il materiale di cui è composta. Questo permette di controllare se è di tipo organico, plastico se contiene acqua, grassi pigmenti oppure è una pellicola fotografica.

Anche un immagine termografica permette di capire se abbiamo di fronte tessuti a temperatura corretta. 
- Permutazioni
Dall'iris CODE non si può ricostruire l'iride ( completamente).

Si possono usare 256! = 10^507 possibili schemi di permutazione ( sulle due iridi da comparare), facendo diventare di fatto il vecchio IRIS CODE inservibile.

È possibile creare IrisCode specifici o permutazioni per ogni singola :
- Applicazione
- Sensore
- Intervallo di tempo….