Introduzione
Si tratta del tratto biometrico meno intrusivo .

Viene utilizzato oggi nella normalità ( face id per sbloccare il cellulare), dalle persone per riconoscersi, è molto apprezzato dagli utenti. Per  i seguenti motivi è molto diffuso.

Può essere catturato da diversi dispositivi/sensori video ( telecamere, webcam).

È molto difficile creare dei sistemi che riescano ad affrontare efficientemente i seguenti scenari :
- Invecchiamento del volto
- Variazione degli sfondi e delle luci in una scena, problema delle ombre sul volto risolto tramite delle reti neurali.
- Espressioni del volto
- Variazioni della posa

Il volto non è uno tra i tratti biometrici più performanti
Il riconoscimento del volto avviene attraverso due approcci :
- Trasformazione :=  EIGENFACES  , Si crea una base di immagini chiamate auto-facce, che permette di ricostruire un nuovo viso come una somma di immagini contenute nella base.
	Non si effettua mai un confronto volto a volto per le differenze elencate nel punto sopra.

- Attributi := Si localizza il volto nell'immagine e si misurano delle caratteristiche come la distanza fra gli occhi, la lunghezza del naso, ecc.. Vengono misurati tratti salienti del viso.
	È possibile distinguere dei gemelli omozigote con il riconoscimento del volto. Ci sono delle variazioni del comportamento rilevate tramite delle reti neurali.


Il tratto biometrico del volto viene impiegato sia per la verifica che per l'identificazione, ma non solo. Molti degli algoritmi non servono solo per produrre sistemi biometrici, ma anche per :
- Riconoscimento facciale delle espressioni
- Riconoscimento del movimento delle labbra  ( anche per multimodalità e controllo anti-spofing)
- Applicazioni di computer grafica
- Creazioni di protesi

Quindi uso non solo biometrics ma anche biometry.

Passive biometrics identification :
Normale telecamere da video sorveglianza  + Surv-tool + face tracking + identification.

La classificazione del volto è divisa in due categorie :
- 2D
	- Immagine fissa
	- Video o tante immagini fisse
	- Colori
	- Toni di grigio
- 3D
	- Scansione laser
	- Illuminazione controllata
Vantaggi :
- Ottimo compromesso fra accettabilità da parte dell'utente e prestazioni in accuratezza.
- Dispositivi di Input facilmente posizionabili ed adatti a molte condizioni operative.
- Risultati direttamente verificabili da un operatore umano
- Permette l'acquisizione non conseziente ( video-sorveglianza)

Svantaggi :
- Alta variabilità intraclasse
	- Illuminazione
	- Posa
	- Occlusioni
	- Sensori
	- Variazioni dell'aspetto dell'individuo  (invecchiamento).  Le variazioni si verificano se consideriamo volti a distanza di decenni, se invece consideriamo un periodo di tempo limitato ( paio di anni) le variazioni sono limitate.
	- Similitudini intraclasse per il volto :
		- Gemelli
		- Fratelli, genitori ( enrollati distanti nel tempo)
		- Sosia: Il DNA contribuisce al 50%, tutta via questo non aiuta, aiuta invece la differenza di età, favorisce la distinzione.
- Un importante competizione indipendente fra algoritmi di FC( face recognition) ha evidenziato il fortissimo impatto delle differenze di illuminazione e posa sulle performance
- Possibile ingannare i sensori non dotati di meccanismi di anti-spofing
- Solo recentemente le accuratezze sono diventate interessanti per sistemi su larga scala.
- Tecnologia matura per i sensori, ma non per gli algoritmi che sono in continua evoluzione.

Fasi Principali, la catena di enroll/ verifica o identificazione di solito consiste nei seguenti passaggi :
- Face Detection ( trovare i volti nelle immagini)
- Face segmentation ( separare il volto dallo sfondo)
- Face tracking ( se in un video deve essere inseguito)
- Face normalization ( crop e normalizzazione della immagine)
- Feature extraction ( grafi, segmenti)
- Matching

Le tecniche di deeplearning ( Convolutinal neural networks), hanno permesso ulteriori passi avanti nelle fasi di :
- Identificazione dei volti ( anche in ambianti non controllati)
- Segmentazione del volto
- Matching

Oggi inoltre trovare un sosia è più facile che mai ( attraverso i social) :

Nel 2022 si sono analizzati i valori di score di 32 coppie di sosia trovate da Brunelle con 3 FR ( Face recognition)  in commercio :
![[Pasted image 20231115094037.png]]

Standard per il template di un volto
L'ICAO e moltissimi governi, hanno iniziato a dettare stringenti regole sulla acquisizione del tratto biometrico ( per passaporti ecc..). Lo scopo è quello di diminuire la varianza intra-classe, arrivando ad impiegare anche per il volto sistemi sempre più accurati.

Tutti i venditori di sitemi biometrici, hanno il loro algoritmo per la creazione del template, spesso segreto e/o sotto brevetto. Di conseguenza non è possibile interoperabilità fra i sistemi , a meno che due stati si passino le foto originali e non il template ( caso opposto di quello delle impronte digitali nel caso delle minuzie) .

L'ICAO, impone da molti anni regole/standard sul formato delle foto per i Machine Redeable Travel Document ( MRTD), per immagini facciali lo standard è il seguente :
- Se è una fotografia a colori scannerizzata, almeno 300 dpi con almeno 90 pixel fra gli occhi.
- Dimensione ridotta a 112 kb con una minima compressione.

Compressione per le immagini facciali :
Il sistema di compressone delle immagini facciali utilizzati sono gli standard JPEG e JPEG2000.

Con questi due algoritmi di compressione si riesce ad avere lo standard di risoluzione di dimensione richiesto della ICAO con 12kb :

Sotto queste dimensioni di memoria, l'immagine è troppo degradata per essere usata con efficacia da un sistema biometrico.
Nei futuri E-passort l'immagine dovrebbe aggirarsi intorno a 15kb-20kb.

Usano la compressione più opportuna di arriva a questi valori per il sample compresso ( non il template) :
- Volto per epassport con JPEG2000: 15kb - 20kb
- Impronte compresse con WSQ 10kb
- Iride compressa : 30kb


VeriLook SDK
Si tratta di un applicazione stand-alone di face recognition. Utilizzata principalmente in applicazioni web ( come modulo).

Permette una identificazione di tipo live-detection, non solo di una faccia ma anche di facce multiple. Presenta una buona accuratezza e una velocità di matching (40.000 volti al secondo)  molto alta sia in verifica ( 1:1) che in identificazione (1;N).

Inoltre i template delle facce, pesano solamente dai 4 ai 7 KB.
Permette inoltre :
- Riconoscimento delle emozioni
- Stima di età
- Tolleranza alla posizione della faccia

Dato che si tratta di un applicazione stand-alone, permette un alta portabilità tra i vari sistemi operativi (utilizzata in più  di 1 milione di applicazioni)


Sensori per i volti 2d
I sensori per la scansione del volto (2D) sono tipicamente basati su CCD ( Charge-coupled device, sensore integrato che converte le immagini in segnali elettrici ). in questa categoria rientrano  :
- Fotocamere
- Telecamere
- Webcam
- Scanner per acquisizioni off-line
- Termografi
- Dispositivi multi-sprettali.

Compariamo la visione della telecamera a colori con quella della telecamera IR, in contesti difficili per il volto ( scarsa luminosità ad esempio)


Face detection
Primo passo della catena, occorre rintracciare il volto/i volti da una scena senza alcun prerequisito particolare. Si tratta di un problema molto complesso, in quanto nell'immagine possono cambiare :
- Condizioni di luce
- Colore
- Posizione dei volti
- Espressione dei volti
- Posa dei volti

I risultati ad oggi migliori si ottengono con degli algoritmi di deep learning. Tutta via è bene notare che non tutte le applicazioni possono permettersi di usare modelli di deep learnign.
Per questo motivo, abbiamo anche bisogno di approcci più "basilari".
Molti approcci sono basati su modelli molto semplici del volto :
- In termini geometrici
- O di texture

Questi modelli permettono di trovare nelle immagini le regioni che fittano meglio il modello dove è maggiore probabilità che vi sia un volto.

L'obbiettivo è quello di individuare il volto / i volti nella scena per arrivare a ricostruire l'immagine sul piano normale a  quello osservazionale attraverso quali :
- Stima dei parametri del volto
- Correzione di scala e traslazione
- Rotazione


Face-Detection Color based :
Nel caso di immagini a colori uno degli schemi più diffusi è il seguente :
- Lightin compensation
- Skin tone detection :
La skin tone detection viene effettuata controllando quali  bit dell'immagine appartengono ad una regione determinata dello spazio colore che evidenza meglio le differenze.

Vengono messi a 1 i pixel che appartengono a una regione dello spazio colore. In questo modo si riesce ad evidenziare il contorno della faccia.
![[Pasted image 20231115094210.png]]

- Localization of facial features ( occhi. Bocca, contorno del viso) :
La rilevazione della posizione degli occhi e della bocca viene effettuata sottraendo immagini espresse in appositi spazi colore ( Y,Cr,Cb) che ne possano mettere in evidenza le caratteristiche cromatiche peculiari insieme a filtraggi morfologici.
- Aggregazione dei risultati


Face detection - Harr feature :
Si tratta di un metodo basato sulle funzioni di haar. Consiste nel cercare nelle immagini, delle regioni che presentano particolari valor delle trasformate di haar.

Solitamente i volti sono caratterizzati da particolari valori e quindi si possono trovare mediante dei classificatori. Le trasformate di haar sono funzioni che prendono il valore di differenze fra i valori di grigio di 2/3 zone ( di area, posizione ed orientamento diverso).

Le posizioni dei massimi ed i massimi delle trasformate sono caratteristiche utili per decidere se è presente un volto nell'immagine di partenza.
Esistono varie trasformate con diversa forma e orientamento.

Quando invece abbiamo un video in input e non più un immagine, allora si parla di face tracking. Non è esattamente come fare face detection in ogni frame, in quanto si hanno maggiori informazioni.
Avendo almeno due frame è possibile effettuare una previsione sullo spostamento del volto.

---

Estrazione delle features :
Feature estratte dalla immagine totale :
- Principal Component Analysis (PCA)
- Indipendent Component Analysis (ICA)
- Linear Discriminat Analysis (LDA)
- Support Vector Machines (SVM)
- Kernel Methods
- Trace traform
- PCANET, CNN

Feature estratte dalla regioni del volto/locali nella immagine :
- Local feature analysis ( LFA)
- Gabor wavelet

Metriche per il matching :
- Distanze euclidee
- Reti neurali
- Elastich brunch graph
- Template matching.


Rappresentazione del volto
Ogni immagine p * q pixel viene rappresentata con un punto nello spazio 
Il problema di tale spazio è che ha un altissima dimensionalità :

Un DB di facce di dimensione p * q crea uno spazio delle facce in !
I metodi di tipo "Apparance based" analizzano la distribuzione delle facce nel face space.

Lo spazio delle facce costruito con immagini row (p*q) ha una dimensionalità troppo elevata, le facce possono risiedere in un sotto spazio limitato. Il modo di stabilire il sottospazio crea il metodo di analisi:

$X_{PCA} = W^tX$

Trovare una trasformazione lineare W che mappa il vettore delle di immagini X in Rn in un sotto spazio di dimensione l molto più limitata l <<n. 
Il matching avverrà sulle feature $X_{PCA}$ e non sulle immagini X. 

Problema : Come possiamo ridurre le dimensione dello spazio e allo steso tempo "separare meglio i punti ?
Prima soluzione è utilizzare la tecnica Principal Component Analysis Pca : O analisi lineare ( nelle domande)

La PCA parte dal riquadro del volto  la mando nello spazio trasformato dalla PCA e vado a togliere alcuni assi meno importanti riducendo la dimensionalità

La PCA per prima cosa cerca una rotazione dello spazio ( ancora la  dimensionalità non cambia) che permette di separare meglio le classi.
In altra parole la PCA cerca una rototraslazione che permette di mettere la variabilità dei dati tutta nei primi parametri.

Notare come varia la distribuzione degli stessi punti sugli assi X = (x1,x2) e Xpca ( Xpca 1, Xpca 2).

La PCA è una tecnica utilissima in molti contesti biometrici. In genere serve a ridurre lo spazio dei dati in ingresso senza bisogno di sapere la label dei dati ( come invece serve nella classificazione).
Permette, partendo da molti dati anche molto diversi fra di loro,  di ottenere un numero minore di nuove variabili molto descrittive.

Vantaggi :
- Decorrela massimamente qualunque insieme di punti nello spazio di uscita Xpca
- Minimizza l'errore quadratico medio tra i dati ricostruiti Xpca e i dati originali X.

Svantaggi :
- Non ci sono algoritmi veloci per la sua implementazione
- È un algoritmo costoso in termini di risorse computazionali per il calcolo degli autovalori e auto-vettori.
- Non usano l'informazione di classe e lavorano solo sulla distribuzione dei punti nello spazio dell facce, indipendementemente se appartengono alla stessa classe o no. Linear discriminat analysis, tecnica basata sulle autofacce che tiene conto della classe di appartenenza.
- Soffrono della variazione di :
	- Illuminazione
	- Posa della testa
	- Alineamento
	- Espressioni facciali

Formulazione della PCA :
Trovare $X_{PCA} = W^tX$ t.c. $W^tSW = V$
Dove :
- X = matrice facce * feauture
- S = matrice di covarianza dei dati
- W = matrice di auto-vettori
- V = matrice di covarianza trasformata, gli autovalori sono $v = [v1,v2,..vn]$

Le facce contenuto nel face space, possono essere analizzate in uno spazio di dimensionalità ridotta.
Inizialmente la PCA esegue una rototraslazione in uno spazio con lo stesso numero di dimensioni, ma gli autovettori non hanno la stessa importanza.
Più è grande il valore dell'auto vettore, maggiore è la sua importanza nella ricostruzione dei dati nello spazio delle feature della PCA ( Xpca)

Autofacce algoritmo :
![[Pasted image 20231115095343.png]]
La PCA ci permettere di calcolare una soglia di distanza fra i punti (facce) nello spazio delle feature utile per il sistema di riconoscimento:
- Dmax = la distanza fra gli utenti più diversi nel DB
- Dmin = la distanza fra i due utenti più simili

Formule :
- Distanza massima fra gli utenti del DB :
$$d_{max} = max(|X_{PCAi}-X_{PCAj}|) \text{ con } i,j =1,2,...,M$$
- Distanza minima fra utenti del DB
$$d_{max} = min(|X_{PCAi}-X_{PCAj}|) \text{ con } i,j =1,2,...,M$$
- Calcoliamo la distanza con l'utente più  vicino fra tutti gli altri utenti del DB (XPCA è l'utente in ingresso)
$$d_{max} = min(|X_{PCA}-X_{PCAi}|) \text{ con } i =1,2,...,M$$

PCA immagine nuova :
Supponiamo che nel nostro sistema biometrico venga fatto l'enrolment di una nuova immagine Z nel sistema :
- Se La distanza dz fra Z e il primo vicino ( C ) è oltre dmax ovvero la distanza mai osservata fra gli utenti nel DB -> non è una zebra.

PCA caso impostore :
Supponiamo che al sistema si presenti un certo utente F ( il quale non è autorizzato ad accedere).
La distanza $d_F$ fra F e il primo vicino ( C ) è :
- Al di sotto di dmax -> Ok, infatti è una zebra
- Ma oltre dimin -> è un impostore.

PCA caso genuino :
Supponiamo che al sistema si presenti un utente D2, il quale è già registrato nel sistema come D e di conseguenza è autorizzato all'accesso.

La distanza dD2 fra D2 e il primo vicino ( D)  è sotto il Dmax ( è una zebra) ed è minore di dmin ( è un genuino con identità D)

È possibile inoltre lavorare nello spazio delle facce :
- Ricostruire una faccia utilizzando le autofaccie :
- Calcolare la distanza dalla faccia ricostruita da quella iniziale :
	L'errore indica quanto l'immagine iniziale era vicina alla immagini con le quali abbiamo calcolato le autofacce.
	Se ricostruisco bene l’immagine nuova (errore basso) allora probabilmente era una faccia somigliante a una di quelle memorizzate, se invece l’errore di ricostruzione è alto allora significa che il volto è troppo diverso rispetto a tutti i volti usati per creare il DB delle autofacce ( genuini)

Enroll  :
Nella fase di enroll a partire dai volti si calcolano le autofacce con la tecnica della PCA.

Verification := Ogni volto del DB può essere riscostruito come una combinazione lineare delle autofacce. Se un nuovo volto viene ricostruito male, allora :
- Non è un volto
- È un impostore


Analisi locale
Lavorano invece sul riconoscimento, misurazione e confronto dei dettagli del volto :
- Misurazione del naso
- Della bocca
- Occhi
- Valori ritornati da particolari funzioni di trasformazione ( gabor wavelet)

Model based
I modelli model based, non estraggono una feautrue singola, ma addatano un modello sulla faccia, ne trovano i coefficenti e vanno a confrontarli con quelli delle facce usare in enrollment
![[Pasted image 20231115095733.png]]
Rientrano nella categoria dei metodi graph matching, in questi modello il volto è rappresentano come una rete di nodi ( feature vectors) sui punti peculiari del volto. Trovato attraverso gabor welvet con diverso orientamento e scala.
![[Pasted image 20231115095746.png]]
Servono almeno due immagini per trovare il modello del volto ( grafo).
La comparazione di due facce è eseguita misurando quanto sforzo è necessario per adattare un grafo tirando i nodi.


Spoofing e anti-spoofing
Il volto può essere coperto da peli o indumenti ( in enrollement o verification). È quindi importante nella fase di enrolment non accettare acquisizioni se la percentuale coperta supera quella necessaria per garantire l'accuratezza certificata dal sistema.

Analizziamo ora i vari tipi di attacchi che possono essere portati :
- Utilizzo di un immagine stampate o di un video.
	Supponiamo di avere un immagine proiettata su uno schermo o stampata di un volto, tecniche di anti-spoofing :
	- Controllo tridimensionalità
	- Controllo sincronia tratti biometrici indipendenti ( esempio variazioni volto e voce durante parlato)
	
	Con un video di un volto proiettato con audio potremmo applicare :
	- Controllo tridimensionalità
	
	In entrambi casi sono possibili le seguenti tecniche difensive :
	- Rilevazione della matrice di stampa o pixel mediante l'analisi della trasformazione di fourier
	- Usare tecniche termografiche o sprettometriche basate su illuminazione a diverse lunghezze d'onda per controllare la presenza di pelle.

- Hill Climbing
	Problema generale : È possibile ricreare un sample da dei template memorizzati in un sistema ?
	Risposta : SI, basta avere accesso al match score
	
	Si usa la tecnica hill climbing :
	- Si inizia con un sample del tutto casuale
	- Si portano delle piccole modifiche di volta in volta che incrementino il match score
	- Si prosegue finchè si riesce ad aumentare il match score.
	
	Supponiamo di partire da un database locale LD di immagini ( alcuni accessi trafugati). Il nostro obbiettivo è quello di manipolare una immagine di partenza per farla matchare con un'altra ingannando il sistema, elenchiamo ora i passi :
	- Partendo dalla immagini Ld creiamo l'insieme di  immagini Efi ( autofacce)
	- Iniziamo dalla immagine che vogliamo Im0 e quella di target Imtarget
	- Facciamo partire l'algoritmo iterativo che modificherà IM0 in IM1, … Imk per assomigliare dal punto del matching a IMtarget
	
	Confidence = la probabilità di corretta verifica per un dato matchscore
	
	Alcuni test mostrarono che è possibile superare il matching con l'immagine generata con probabilità del 99.9 %, qualunque sia il valore di soglia settato per il matching con n iterazioni prima o poi si entrerà.
	Ripetendo per N volte l'algoritmo e creando l'immagine media dai vari risultati si ottiene un sample sempre più vicino a quello di target.
	
	Partendo da una faccia diversa posso ottenere una immagine simile a quella usata in enroll.
	
	Per contrastare l'attacco è stato proposto lo standard BIOAPI :
	- L'idea di base è che molte modifiche all'immagine non produrrebbero cambiamenti nel match score, quindi l'algoritmo non saprebbe come arrampicarsi sulla collina.
	- Risultato : le tecniche modified hill climbing funzionano lo stesso

- Controllo istogrammi colore : Il controllo avviene controllando al distribuzione dei colori negli istogrammi.


Alcuni metodi anti-spoofing
Il sitema chiede all'utente di fronte al sensore di pronunciare una frase ( casuale ) richiesta dal sistema.
Il sistema misura la variazione dei movimenti delle labbra nel tempo controllando se si sta cercando di ingannare il sistema con un fantoccio/maschera/immagine proiettata.

Esistono anche delle variazioni di questi sitemi ( volto + labbra). Il sistema BIOID aumenta l'accuratezza della identificazione controllando i movimenti delle labbra mediante il flusso ottico fra 2 frame adiacenti.

Facial Fingerpting :
Si iniziano a sviluppare progetti per sensori e tecnologie per il facial fingerprinting ( non near IR).
Viene costruita una mappa dei capillari al di sotto del volto, essa può essere rilevata da telecamere ad infrarosso ad alta risoluzione, diventando un nuovo tipo di tratto biometrico :
- Assolutamente unico
- Difficilmente falsificabile
- Non intrusivo
- Assolutamente accurato

Può funzionare come mappa 2D ma sarà possibile arrivare alla mappa 3d

Utilizzo di telecamere IR :
La diffusione di telecamere nel vicino infrarosso è piuttosto elevata.
La visione IR offre un punto di vista diverso e più robusto rispetto alle condizioni ambientali.

I display o le superfici stampate in visibile diventano non usabili per attacchi con camere near IR

---

Sistemi 3D
I sistemi biometrici sul volto 3D attualmente disponibili sono in grado di gestire correttamente :
- Acquisizioni frontali
- Con espressione neutra

Altri studi sono attivi per fare riconoscimento a distanza ( long-range 3D face recognition).
L'acquisizione 3D di un volto può svolgersi nei seguenti modi :
- Scanner laser
Una lama di luce laser scandisce il volto del soggetto durante una ripresa video.
Attraverso la geometria spaziale del sistema, si ricostruisce la superfice dalle "fettine" presenti in ogni frame filmato.
Occhi chiusi

- Luce strutturata
Si illumina il volto da riprendere, con un proiettore in grado di produrre una fascio di luce strutturata ed una/due telecamere.

Con i sistemi code light, si proiettano in successione tanti pattern binari con bande sempre più fini. Il sistema ricostruisce la tridimensionalità usando la deformazione delle bande nell'immagine.

Per aumentare l'area della superficie 3d acquisita si possono usare due tecniche :
- Si usano due telecamere
- Si producono due acquisizioni indipendenti "coded light". Ottenute due diverse code light si uniscono per ottenere un'unica superficie 3d.

- Mediante viste
I sistemi chiamati 2,5d, riescono a riprodurre la superficie 3d del volto da tane immagini del volto prese da angoli diversi, usando una normale telecamera.
Con un passaggio successivo, altri sistemi riescono a ricostruire un vero modello 3D del volto partendo dalle immagini 5D.

N.B = i face modeler che applicano la faccia 2D su un modello 3D standard uguale per tutti non possono essere utilizzati per scopi biometrici. Ecco perché costano poco.
Vengono utilizzati nel campo del 3D per prove e scelta di accessori.


Vantaggi del 3d :
- Invarianza alla luce e all'ambiente ( usano luce IR propria), posa e makeup
- Sono maggiormente tolleranti rispetto a colori di sfondo, accessori, trucco del viso
- Invarianti rispetto a piccoli spostamenti angolari del volto
- La precisione di alcuni sistemi permette di distinguere due gemelli omozigoti.
- Capcità realtime
- Bassi valori di FRR ( false reject rate), anche se il false match rate è molto basso
- Dislocazione del sensore : Esistono in commercio dei sensori base di dimensioni ridotte che possono essere alloggiati in ogni situazione, muro, porta/cancello, sensore portatile.

Svantaggi del 3D:
- Costo dei sensori e dei sistemi maggiori
- Il soggetto deve essere collaborativo

Esempi di sistemi in commercio :
- RealSense D435 camera
Riconoscimento biometrico : 3D, colore, punti fiduciari.
Permette il riconoscimento delle emozioni e delle espressioni ( ottenuto combinando  il sensore con librerie come openCV).
- Face id di apple
- Macchina vision 3D + 2D ICAO
Si tratta di un sistema usato per enrollment, verification e identification di immagini facciali 3D e 2D.
Il sensore acquisisce simultaneamente il 3D e il 2D rispettando le specifiche ISO.


2D vs 3D

I sitemi 3D pur non garantendo una completa invarianza rispetto alle variazioni del volto presentano una situazione migliore. Nessun sistema basato sul volto assicura una completa invarianza rispetto a i fattori temporali.
![[Pasted image 20231115100358.png]]

Tabella delle tolleranze.
Alcuni parametri per la scelta di un sistema 3D oppure 2D :
- I sistemi proposti hanno costi e accuratezze diversi.
Il costo dei sensori varia da poche centinaia di euro a oltre 10.000 euro

- Un medico potrebbe avere bisogno di una ricostruzione al decimo di millimetro di un volto per fare una protesi (3D)
Un sistema biometrico al contrario può richiedere meno errore sulla misura, ma maggiore sarà la misura, migliore sarà l'accuratezza del sistema finale .

- I sistemi si scelgono tenendo conto di :
	- Risoluzione in mm sulla superficie
	- Della accuratezza in mm della superficie
	- Tempo di acquisizione e di elaborazione
	- Del tipo di luce richiesta sia ambientale che per la proezione
	- Del gradimento da parte dell'utente

Algoritmi di matching 3D
Avendo a disposizione sensori 2D e 3D non è detto che non si possano usare congiuntamente

Schema delle possibilità attualmente possibili :
![[Pasted image 20231115100500.png]]
Il confronto fra due volti con tecniche 3D presenta i seguenti passaggi :
- Se il volto 3D non è direttamente acquisito dal sensore, allora da multiple stils si ottiene la rappresentazione 3D dei volti da confrontare ( tipicamente uno dei volti è già stato memorizzato in fase di enroll)
- I volti vengono sovrapposti (rototraslati) fino a trovare la migliore sovrapposizione delle superficie
- Si valuta il grado di sovrapposizione con una soglia. Il match prevede l'individuazione di 3 punti di riferimento nelle immagini per facilitare la corretta sovrapposizione.

Per approfondire i risultati ottenibili da queste tecniche ci dobbiamo riferire solo a prove comparative indipendenti (dai produttori) sui dati pubblici e non rilasciati prima dei test ( secretati). In ogni caso abbiamo i seguenti risultati :
- FAR (false accept rate) fissato a 0.001 tra tutti i partecipanti. Viene misurato il tasso in verifica. Quante volte il sistema sbaglia nel dire tu sei tu.
- Windows hello face autentication FAR = 0.001% 5% FRR  :
Alcuni aspetti interessati di questo sistema :
- Vengono utilizzate delle caratteristiche facciali locali, l'algoritmo prende centinaia di sample da aeree differenti della faccia. Nessuna immagine della faccia viene memorizzata. Si tratta di un sistema a feauture locali
- La rappresentazione deve passare un modello di machine learning prima che l'algoritmo di matching lo identifichi come genuino. In caso di autenticazione ( con pochi utenti del sistema) la soglia di matching viene alzata.

I passi futuri riguardano la funzione multimodale e l'uso delle reti neurali.


Confronto con umani
Uno degli obbiettivi è quello di arrivare a eguagliare o superare il tasso di riconoscimenti degli umani.
Si è creato il seguente insieme di confronti :
- 240 coppie di facce, 120 maschi e 120 donne 50% facili e 50% difficili
- Diverso colore e lunghezza dei capelli
- Diverse condizioni dello sfondo

Gli umani potevano rispondere con :
- Sono sicuro che siano la stessa persona
- Penso siano la stessa persona
- Not sure
- Penso non siano la stessa persona
- Non sono la stessa persona

3 algoritmi su 7 sono stati capaci di fare meglio dei supervisori umani sul dataset difficile.

Mentre tutti hanno fatto meglio dell'uomo su dataset facili.


Critiche verso il Face recognition
Nel FR si stanno notando grandi miglioramenti in :
- Accuratezza
- Usabilità
- Numero e tipo di dispositivi dove poterlo applicare

Tutta via l'utenza è preocupata riguardo alla sua diffusione e alla privacy :
- Molte associazioni di utenti stanno chiedendo di rifiutare l'uso della sorveglianza biometrica negli spazi pubblici
- Alcuni fornitori come ibm, hanno deciso di non fornire più le tecnologie di FR di massa a organi di polizia e municipalità.

Gli errori ( FNMR, FMR, CMC) sono tutta via ancora abbastanza alti da creare un effetto di protezione da "errore del sistema" su schedature a scala metropolitana e nazionali nel FR.
In EU, tutta via, è ancora aperto il dibattito se utilizzare o meno queste tecnologie in screening di massa.



EER  = punto sulla curva det in cui FNMR = FMR
Avevamo indicato fra i principali fattori migliorativi del volto :
- Alta risoluzione delle immagini
- Multi-stil, multiple shots
- Introduzione dei dati 3d
- Artificial intelligence

Controllo del volto 3D usando un sistema 2D.

Partendo dal sensore più semplice, ovvero la camera visibile 2D è possibili eseguire shape from motion.

![[Pasted image 20240214090426.png]]

- Zoom := si tratta di una tecnologia che a partire da un immagine frontale del volto, ( la zona centrale è quella del volto che ha maggiori dettagli 3d utili), costruisce un modello 3D.

Viene realizzato un modello 3D, a partire da camere 2D, tutta via il modello 3D contiene più dati rispetto ad un qualsiasi foto piatta.

Il test di matching viene fatto su immagini 2D.

- FAR 1/4,200,000 FAR @ less than 1/100 (FRR)

- 668% better than the top algorithm in lates NIST’s FRVT results. Risultati rilevati mediante test proprietari e non indipendenti.

- Sempre il produttore afferma che si tratta di una tecnologia molto robusta alle frodi, perfino agli utenti dormienti con occhi chiusi.

Resiste a :
- Maschere
- Video ad alta risoluzione
- Progetti video su teste 3D
- Impostori, sosia.

- 3D face Map := si tratta di una tecnologia, la quale partendo da un video di 2 secondi permette di verificare :
	- Vitalità del volto
	- 3D della superficie
	- Riconoscimento del volto 3D.

Inoltre gode delle seguenti caratteristiche :

- Interoperabile .= funziona con tutte le camere dei cellulari recenti
- Controlli di liveness veloci
- Funziona in condizione ambientali realistiche
- Funziona anche con occhiali, barba, trucco.

Spoofing e anti - spoofing volto 3D
Struttura generale dei metodi anti spoofing :
![[Pasted image 20240214090439.png]]
Alcune tecniche per frodare un sitema 3D :
- Nel campo delle protesi e dei materiali sintetici che emulano il corpo umano sono stati fatti grandi passi. 3D printed Latex mask.
- Maschera con ritagli per gli occhi := un attacco con maschera con ritagli per mostrare gli occhi. Tale attacco viene individuato da "salti" del flusso ottico casusate dalla discontinuità dei fori fra le parti mobili (occhio) e fisse (maschera).

Possibili controlli :
- Usando illuminatori a lunghezza d'onda è possibile avere in tempo reale ( parziale) analisi  spetto grafica del volto . Inoltre attraverso dei sitemi di classificazione che analizzano i dati spetto-grafici si stima il materiale di cui è composto :
- Tipo organico, se contiene acqua, grassi
- O plastica, gomma, silicone
- Usando sensori termici, permettono un analisi termografica dell'immagine. Permettono di capire se abbiamo di fronte dei tessuti a temperatura corretta ( tutta via il costo dei sensori termografici sta rapidamente scendendo nel tempo)
- Battito delle palpebre := Avendo un sensore con elevati FPS (>30) e risoluzione è possibile verificare :
- Assenza di pattern ed effetto Moirè
- Movimento delle palpebre compatibile per direzioni ed entità a quello naturale.

Lo scopo del flusso ottico è quello di assegnare ad ogni pixel appartenente al frame corrente un motion vector che punta verso la posizione dello stesso pixel in un frame di riferimento successivo .