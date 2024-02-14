Introduzione
La mano è un tratto biometrico molto ben accetto dagli utenti perché poco invasivo.

Offre un discreto livello di accuratezza, discreto in quanto non è possibile distinguere univocamente un individuo dalle dimensione delle sue mani, per questo motivo offre la possibilità di lavorare in modo multimodale ( si controllano più aspetti, lavoro con più tratti biometrici  ).

Di solito si lavora su tre viste:
- Palmare
- Dorsale
- Laterale

Possiamo quindi estrarre in questo modo molte informazioni biometriche, permettendo di identificare meglio un individuo.

Tratti rilevati tramite :
- Scanner
- CCD camera ( media risoluzione)

Approcci per il riconoscimento :
- Misura delle lunghezze
- Confronto delle immagini e delle parti
- Studio delle linee


Caratteristiche del tratto biometrico :
- Tratto biometrico moto ben accettato dagli utenti perché poco invasivo : È normale porgere la mano o darsi una stretta di mano quando si incontrano due persone.
- Presente fin dal 1979 sul mercato ( tecnologia matura)
- Offre un discreto livello di accuratezza, senza dover chiedere all'utente sample molto critici perla privacy come l'iride o l'impronta.
- Offre la possibilità di funzionare in modo multimodale, controllando più aspetti come immagini, misure, pattern delle vene.
- Diffusione sul mercato buona :
	- Impronte (44%)
	- Face (19%)
	- Geometria della mano(9%)
	- Iride(7)
	- Voce(4)
	- Firma(2)
	- Multimodali(4)
- L'utente deve essere collaborativo
- Dalla mano sono estraibili circa 90 features :
	- Misura delle lunghezze degli elementi
	- Confronto delle immagini
	- Immagine termica per pattern vene
	- Studio delle linee della pelle

Sono sistemi veloci, adatti per essere affiancati a tornelli, porte e cancelli. Vengono utilizzati principalmente per il controllo degli accessi.

Sono sistemi impiegati anche per applicazioni del tipo "time and attandance" cioè per il controllo delle presenze sui luoghi di lavoro.

La geometria della mano è il tratto biometrico preferito dal garante della privacy.
Vantaggi :
- Tecnologia consolidata
- Sensore robusto
- Dimensioni del template motlo ridotte
- Minore impatto sulla privacy degli utenti

Svantaggi :
- Costo circa sui 1000 dollari
- Dimensione e peso notevoli
- Sensibilità a forte luce diurna

Sensori :
Di solito si lavora su tre viste :
- Palmare
- Laterale
- Dorsale

Vengono utilizzati scanner ( anche < 1800 dpi), CDD camera ( media risoluzione) visibili o ad infrarossi.

Possiamo inoltre distinguere i sensori in due categorie :
- Sensori con guide := il sistema diventa più accurato perché si riduce la variabilità intraclasse del sample, essendo forzato ad assumere una posizione corretta.
- Sensori senza guide := con i pioli l'utente deve imparare il corretto posizionamento della mano.

Inoltre si stanno iniziando a diffondere sistemi contactless ( come ad esempio quello di amazon one).

Passi per il matching
- Peg Removal := conoscendo la posizione fissa dei pioli è facile sottrarli alle immagini per avere a disposizione solo la mano.
- Estrazione dei contorni := si usa un algoritmo a soglia adattiva per segmentare l'immagine e trovare il contorno esterno della mano.
- Estrazione delle dita ed allineamento := ile 5 dita vengono estratte dal profilo ed allineate separatamente a partire da posizioni standard. Questo rende il matching maggiormente veloce.

- Matching :
	- Le curve delle due mani da confrontare gia allineate sul riferimento vengono trasformate in gruppi di punti
	- Il matching lavora individuando coppie di punti e misurando la loro distanza. La loro distanza media è chiamata mean alignment error ( MAE)
	- Se il mae è minore di una soglia prefissata l'utente è considerato un genuino altrimenti come impostore.

Eigenfingers := in modo assolutamente simile al metodo delle autofacce da un database di immagini di mani, è possibile ricostruire le dita ed il palmo.

Ad oggi non si ha notizia di comparazioni indipendenti dal produttore di algoritmi e sistemi biometrici basati sulla mano, simili a quelli per il volto ( FRVT) ecc…

Un test governativo ( INPASS Evaluation),  ha rilevato le seguenti performance :
- FTE = 2% ( failure to enroll)
- FNMR = 1,5 % FMR = 1,5 %
- ERR = dal 3 al 1.5 %  punto della curva det in cui FNMR = FMR riassuma dal punto di vista generale l'andamento di un sistema biometrico.


Riconoscimento del palmo
![[Pasted image 20240214092622.png]]

Touch-Based system :
- Maggiore accuratezza
- Si lasciano impronte sul device
- Compatibili con classici sistemi di impronte
- Minore usabilità

Touchless :
- Minore o uguale accuratezza
- Non si lasciano impronte sul device
- Maggiore usabilità
- Parziale compatibilità con i sistemi classici.

Si tratta di sitemi biometrici che lavorano sul palmo della mano, hanno un raggio d'azione che parte dall'inzio del polso e arriva fino alle dita, Diverte feauture estraibili con diversa risoluzione :
- Feature geometriche
- Linee principali
- Delta points
- Minutiae
- Level3 features

| Risoluzione | Livello feauture estraibili | Descrizione |
| ---- | ---- | ---- |
| 300 | Livello 1 | Linee del palmo |
| 500 | Livello 2 | Minutiae |
| 1000 | Livello 3 | Pori |

Tra 300-500 dpi è la tipica zona d'azione del palm ricognition.

I moduli di matching sono ad HOC in base alle features estratte vanno da semplici metriche euclidee fino a funzioni complesse con deep learnign.

![[Pasted image 20240214092720.png]]

Touch based 2D :
- Approccio moto simile alle impronte, di conseguenza molti sensori (scanner) sono multifunzionali e possono acquisire anche le impronte.
- Si lasciano le tracce delle impronte sullo scanner ( impronte latenti )

2D palmprint touchless
A differenza dei touched base sono dei sistemi less-constrained
E richiedono minori dpi per una corretta scansione.
- Minor cooperazione richiesta
- Tendono ad avere una minore o uguale accuratezza rispetto ai metodi a contatto.
- I template estratti non sono compatibili con la maggior parte dei sistemi a contatto
- Presentano una maggiore usabilità
- Non lasciando impronte digitali sulla superfice del sensore

Ad oggi vengono ad esempio utilizzati per acesso logico ai terminai, oppure per accesso fisico ad aree ristrette.

Svantaggi :
- Funzionalità ad alta precisione non sempre utilizzabili ( minuzie)
- Sensibili agli sfondi, alla illuminazione e ai cambi di posa ( mano troppo vicina o lontana dal sensore)

È possibile utilizzare dei sensori IR per il riconoscimento delle vene, in questo caso non stiamo più parlando di palm recognition ma di vein palm biometrics:

Parliamo di un tipo di acquisizione unconstrained  se abbiamo un sensore senza guide. Tutta via possono essere usate delle particolari guide sui sensori per garantire la corretta distanza lavoro, richiede più cooperazione da parte dell'utente ma garantisce anche una maggiore accuratezza.

Possibili attacchi tramite appositi calchi in cera.

FRR ( false reject rate) = 0.01

3D palm recognition
2D vs 3D :
- Vantaggi  del 3D :
	- Robusto per illuminazione, occlusione, rumore
	- Resistente alle fordi
	- Invariante alla posizione alla distanza
- Svantaggi :
	- Dispositivo più complesso
	- Costoso

Acquisizioni del palmo 3D :
- 1 telecamera -> N acquisizioni nel tempo -> Dati 3D
- 2 telecamere -> 1 acquisizione multipla -> Dati 3D

Al momento sta venendo ancora sviluppato il primo sistema contactless commerciale per pali e impronte 3D