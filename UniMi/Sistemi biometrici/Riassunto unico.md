Overview
Cosa ci da la biometria in più :
- La biometria ci offre un nuovo modo, automatico, di identificare le persone.
Si passa da una cosa che sai ( password) o da  una cosa che hai ( chiave, carta, documento) ad una cosa che sei ( iride, impronta) o quello che fai ( firma, voce).

Abbiamo due possibilità di identificazione in più in base a cosa sei o casa fai ( il tuo comportamento, le tue azioni).

Definizione di Biometria: insieme di tecniche automatiche per il riconoscimento degli individui basato sulle loro caratteristiche fisiche e comportamentali.

Riconoscimento della entità := Operazione che associa una identità ad un individuo.

Il riconoscimento può essere suddiviso in due categorie :
- Verifica dell'identità ( autenticazione)
	- Equivale alla domanda : sono chi dico di essere ?
	- Conferma o nega l'identità dichiarata dall'utente
	- Metodi one to one (1:1)
- Ricerca dell'identità ( identificazione)
	- Equivale alla domanda chi sono io ?
	- Al sistema biometrico non viene presentato nulla, e a carico del sistema riconoscere l'identità dell'utente che si presenta, verificando che sia presente nella lista degli utenti ammessi.
	- Metodi one to many (1:N)
	- Il problema di identificazione può essere :
		- Chiuso ( insieme di utenti del sistema prestabilito)
		- Aperto ( videosorveglianze)  molto più difficile, l'insieme N si allarga.

Queste due categorie hanno diverse funzioni e complessità di realizzazione diverse.
Di conseguenza tali categorie, autenticazione e identificazione non sono equivalenti

- Abbiamo una autenticazione/identificazione Positiva  = Quando si cerca di stabilire con elevata accuratezza che l'utente sia chi dice di essere.
- Abbiamo una autenticazione/identificazione Negativa := Quando si cerca di stabilire con elevata accuratezza se l'utente non è chi dice di essere

Alcuni esempi :
Identificazione Positiva = Un sistema di accesso ad un sito militare controlla la mia iride per controllare se appartengo ad una lista di utenti abilitati all'ingresso.
Identificazione negativa = Un sistema di visione controllata con delle  telecamere se chi passa davanti agli obbiettivi non sia un terrorista presente in una lista.

Metodi Classici di Autenticazione
- Possesso ( qualche cosa che possiedi), di solito chiamate anche token base.:
	- Puoi entrare in laboratorio se hai la chiave .
	- Puoi ricevere i soli da una banca con un assegno circolare.

	Problematiche associate, il token o la chiave possono essere  :
	- Persi o rubati
	- Prestati a chi non dovrebbe utilizzarli
	- Usati in contesti non autorizzati

- Conoscenza (qualche cosa che sai)  di una porzione di informazione
	- Puoi accedere al sistema se conosci una login ed una password associata ad una persona autorizzata ad entrare.

	Problematiche associate, la password può essere :
	- Dimenticata
	- Ceduta/trasmessa ad altri
	- Individuata per tentativi ( attacchi di tipo brute force), semplice se la password è facile da ricordare ( nome del cane, data di nascita, ecc..)
	- é stato calcolato che in media che un individuo deve ricordarsi oltre 20 password/codici, di conseguenza si tende ad usare la stessa password più volte.

- Alcuni sistemi funzionano integrando le due modalità := usi il bancomat se HAI la carta e CONOSCI il pin.

- Metodi biometrici :
Il riconoscimento avviene in base alle caratteristiche fisiche e/o comportamentali dell'individuo. ( Tratti fisici come iride, impornta, geometria della mano, volto. Tratti comportamentali come voce, firma)

Vantaggi :
- I tratti biometrici, sono sempre con te, non possono essere dimenticati o utilizzati da altri.
- E molto più difficile falsificare un tratto biometrico che un documento o una chiave.
- L'accuratezza della identificazione ( livello di sicurezza raggiunto), può essere molto più elevata rispetto ai sistemi tradizionali.
- Possono essere combinati con i metodi tradizionali
- Solo i metodi biometrici possono effettuare un identificazione negativa," il sitema dice che io non sono lui"
- Si tratta di sistemi che godono della proprietà di non ripudio. "sono innocente, qualche altra persona ha usato il mio PIN " ) .

Svantaggi :
- I sistemi biometrici hanno un costo maggiore
- I sitemi biometrici rispondono in realtà con un livello di matching e non con una decisione binaria "yes/no"
- Alcune persone li vedono come un invasione della propria privacy, non vogliono essere schedati.
- Non possono essere cambiati a piacimento, a differenza di una password, la quale può essere facilmente cambiata.
- Alcune persone con delle disabilità, potrebbero non disporre di alcuni tratti biometrici ( voce, impronte digitali usurate, iride) 

Confronto tra le 3 modalità :
- Metodi basati sul possesso := Qualcosa che si possiede, si tratta di metodi di autenticazione molto semplici da implementare ma il livello di sicurezza raggiunto è anche molto basso.
- Metodi basati sulla conoscenza := Qualcosa che si sa, si tratta di metodi mediamente difficili da implementare, il livello di sicurezza raggiunto è più alto rispetto ai metodi basati sul possesso.
- Metodi biometrici := Si tratta delle tecniche più difficili da implementare, ma anche quelle con il maggior livello di sicurezza.

Proprietà di un tratto Biometrico
Le proprietà che un tratto biometrico deve avere sono sei :
- Universalità := Ogni persona deve possedere un certo tratto / caratteristica
- Unicità := Due persone non devono avere lo stesso tratto uguale
- Misurabilità = il tratto deve poter essere esaminato quantitativamente
- Performabilità = Accuratezza della identificazione che deve essere adeguata e deve poter essere garantita senza particolari condizioni operative .
- Accettabilità = percentuale di persone che potrebbero accettare l'uso di un particolare sistema biometrico
- Circonvenzione = Grado di difficoltà nell'ingannare il sistema con apposite tecniche fraudolente.

Differenza tra Biometrics and Biometry
BIOMETRICS := Metodi di identificazione ( automatica) basati sulle caratteristiche fisiche e comportamentali dell'individuo.
BIOMETRY := Campo si studio molto più ampio che comprende l'applicazione della statistica alla biologia e alla medicina.

Trend del mercato globale biometrico :
- Possiamo osservare come siamo passati da un mercato, dal valore di 45.6 milioni di dollari nel 2021, ad un mercato stimato dal valore di 137-5 milioni nel 2030. Abbiamo di conseguenza una crescita nei vari anni.
- Possiamo Inoltre osservare come la percentuale di cellulari dotati di sistemi biometrici sia aumentata dal 2016 al 2020, passando da un 68 % ad un 80%


Funzionamento Generico sistema biometrico basato sull'impronta digitale
Possiamo considerare i sistemi biometrici come sistemi di pattern recognition ( non è presente la fase di coding).

Si struttura in due fasi principali :
- Enrollment := Fase di inserimento. Il tratto biometrico viene per la prima volta acquisito dal sistema e registrato oppure viene creato il documento biometrico.
- Identificazione / verifica := Fase di riconoscimento. Il tratto biometrico viene nuovamente acquisito. Se risulta sufficementemente aderente alle informazioni registrate nel sistema biometrico l'accesso è consentito.

Schema del funzionamento :
![[Pasted image 20231106092049.png]]
- Acquisition := l'importa digitale viene acquisita.
- Feature extraction := dall'impronta vengono una serie di tratti distintivi
- Coding = vengono "codificati " e salvati nel database.
- Può essere stabilità una certa soglia, se il matching è al di sotto della soglia l'utente non è abilitato ad utilizzare il sistema.


Tratti biometrici : Caratteristiche
Tratti biometrici maggiormente diffusi e determinati :
- Impronte
- Facce
- Iride
- Geometria della mano
- Voce
- Firma
- Sistemi multimodali

Ogni tratto biometrico viene analizzato fino ad estrarne un insieme di caratteristiche che una volta codificate compongono un template.
Esempi di template: IrisCode, Lunghezza delle dite di una mano, Coordinate nel tempo di una firma, Posizione delle minuzie di una impronte

- Impronta digitale
Si tratta di uno dei tratti biometrici più diffusi e più antichi del mondo.
L'impronta digitale è un pattern di creste e valli che si sviluppa da una configurazione causale già presente dall'embrione.

Ad oggi si ritiene che siano uniche (non sono mai state trovate due persone diverse la cui impronta possa essere scambiata) e che non cambino nel tempo, la disposizione resta la stessa.

Soddisfa dunque le proprietà di un tracco biometrico.

Identificare se un impronta è la stessa rispetto ad una già registrata è un problema di pattern matching molto complesso.
Si utilizzano vari tipi di sensori per identificare un individuo tramite la sua impronta.

È inoltre molto difficile progettare sistemi che riescano a :
- Funzionare anche con diverse condizioni della pelle (sudore)
- Funzionare anche con piccoli overlap ( interruzioni nell'impronta), sovrapporre due impronte potrebbe risultare difficile.
- Aumentare la qualità del sample rilevato, qualità dei tratti diverse.

Il riconoscimento avviene tramite tre diversi approcci :
- Correlation-based := Algoritmi che permettono di fare delle correlazioni tra due immagini, verificano che parti dell'immagine siano simili.
	Troppo semplice, lontano dagli standard odierni. Adatto per sistemi di piccole dimensioni.

- Minutia-based := Si tratta di "fenomeni" particolari che avvengono sui ridge. Vengono utilizzati in particolare per l'analisi le biforcazioni dei ridge e dove si interrompono. Riconosciamo l'impronta per una particolare disposizione dei punti particolari.
	Metodo più utilizzato.

- Ridge feauture based  := Algoritmi che analizzano nel dettaglio la struttura delle singole creste/valichi che costituiscono un impronta.
	Ridge = venature dell'impronta


- Volto
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


- Mano
Tratto biometrico molto ben accetto dagli utenti perché poco invasivo.

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


- Iride
Considerato il tratto biometrico più accurato, tuttavia viene anche percepito come il tratto più invasivo.

Più differenze trovo in un tratto biometrico, più esso è forte.
L'iride presenta numerose caratteristiche stabili nel tempo, di conseguenza è molto forte. Rende una persona riconoscibile negli anni.

Tuttavia creare un sistema di riconoscimento è costoso ma difficile da ingannare

Può essere rilevato tramite sensori più o meno costosi :
- In ambito professionale sono utilizzate i CDD oppure ottiche speciali.

Un sistema di riconoscimento dell'iride possiede una serie di algoritmi che devono :
- Trovare l'occhio nel viso .
- Scattare e confrontare più frame per verificare se l'iride è viva, non sto cercando di frodare il sistema .
- Selezionare la parte utile.
- Eliminare i riflessi e le ciglia .
- Compensare le deformazioni dell'iride le quali possono presentarsi in condizioni di luce differente. Viene tolto tutto quello che non è biometrico.

Identificare l'iride è un operazione molto difficile.

Come agisce un algoritmo di riconoscimento :
- Da una foto del volto si cerca di selezionare solo l'occhio
- Vengono tagliate le palpebre.
- Viene presa la pupilla e il diametro esterno
- Vengono tolte ciglia e riflessi
- L'iride viene selezionata tramite un canale ad infrarossi
- L'immagine rotonda dell'occhio viene stesa rendendola rettangolare.
	A questo punto viene generato l'iris CODE, si va a vedere le differenze di toni di grigio tramite un algoritmo, le quali generano una stringa, generando un pattern dell'iride.

Le lenti ottiche, lenti a contatto, non permettono il riconoscimento dell'iride.

L'iride insieme al volto costituisce un super tratto biometrico. Permette di tracciare una persona nel tempo attraverso una foto. Per questo motivo devono essere opportune leggi sulla privacy.


- Firma
Si tratta di un metodo molto diffuso e semplice.
Tuttavia abbiamo una bassa accuratezza.

A differenza dei sensori per la rivelazione dell'iride tutta via il costo del sensore è estremamente basso. I sensori possono essere dei pad più complicati, per misurare varie velocità nella firma, firma dinamica. Oppure dei più semplici schermi touch firma statica.

Come avviene il riconoscimento ? Esso avviene sugli andamenti nel tempo di una serie di valori , viene misurata la dinamica della firma:
- Delle coordinate x, y
- Della pressione
- Dell'azimut
- Dell'inclinazione


- Voce
Tratto biometrico accettato dagli utenti. Può essere utilizzato in modo continuo ( è uno dei pochi ), mentre continuo a parlare un sensore potrebbe continuare a rilevare il tratto biometrico.

Tuttavia abbiamo una bassa accuratezza ma un moderato costo, è inoltre abbastanza facile da frodare.
Il template deve essere di grandi dimensioni.

La voce è biometrica in quanto ognuno parla nel proprio modo, Ci sono delle differenze fisiche,  ( differenze muscolari tra polmoni, corde vocali, laringe, faringe). C'è inoltre un secondo strato che riguarda il comportamento dell'individuo, differenze corporamentali  ( accento, modo di esprimersi)


Sistemi Multimodali vs Monomodali
I sistemi multimodale hanno il compito di unire più tecnologie biometriche  in un sistema ( non si tratta solo di unire più tratti biometrici)

L'obiettivo è quello di aumentare l'accuratezza e la robustezza alle frodi.

Un sistema multimodale può essere composto in diversi modi :
- Diversi tratti biometrici
- Multiple finger system
- Impressioni multiple, ovvero più misurazioni. Dalle misurazioni estraiamo informazioni diverse dello stesso tratto biometrico.

Soft Biometrics
Alcuni tratti biometrici non posseggono le 7 caratteristiche necessarie ma possono essere usate in aggiunta per l'identificazione di un utente. Esempi di soft biometrics :
- Genere
- Colore della pelle
- Colore dei capelli
- Colore degli occhi
- Peso
- Altezza


Storia della biometria
Gli animali si riconoscono fra di loro in modo biometrico :
- Livrea, Aspetto, forme
- Verso
- Odore
- Comportamento

Delle prime forme di riconoscimento e autenticazione gli abbiamo con gli assiri (2500 A.C) , i quali usavano sigilli di argilla contenenti anche l'impronta dei funzionari per firmare documento legali :
- Riconoscimento := le impronte criminali vennero impresse in tavole di argilla a foni identificativi
- Autenticazione := le incisioni cuneiformi presentavano l'impronta digitale dell'autore per evitare contraffazioni.

i cinesi negli anni nel 300 A.C usavano sigilli di argilla con l'impronta digitale per firmare documenti legali e per registrare criminali. Successivamente vennero utilizzate la seta e l'inchiostro.

Il primo sitema di identificazione biometrico ( anche se non automatico), viene inventato nel 1882 da Bertillon.

Bertillon, creò un innovativo sistema per identificare i criminali basato su delle misurazioni antropometriche :
- Lunghezza del braccio e delle dita
- Altezza e larghezza della testa
- Lunghezza dei piedi

L'ipotesi  di Bertilon, era che tali misurazioni potessero identificare univocamente un individuo nel tempo, per i seguenti motivi :
- Lo scheletro umano non si modifica dal 20 anno di età
- Ogni scheletro è diverso quindi dai dati si può risalire ad un identità.

Come per i moderni sistemi biometrici, abbiamo due fasi :
- Fase di enrollment := Ogni persona viene registrata attraverso una scheda con fotografia.
- Fase di matching := le ricerche erano ovviamente manuali.

Successi del sistema :
- Il sistema nel suo periodo storico di diffuse in tutto il mondo.
- Fu utilizzato circa fino al 1896.

Fallimenti del sistema :
- Le troppe categorie per dividere le schede (246) rallentavano le ricerche fino a parecchie ore per sistemi con molte schede.
- La non accuratezza  delle misure dei criminali adolescenti, poi crescevano
- L'arrivo delle impronte digitali negli USA, anni 90
- Il caso west 1903 :
Will WeSt viene imprigionato e schedato con il metodo bertillon. Si scopre che le sue misure e le sue fotografie sono già presenti in archivio, corrispondono perfettamente ad una scheda.

Will west, tutta via dichiara di non essere mai stato schedato fino a quel momento, dopo accurate indagini emerge che la scheda che ha effettuato il matching apparteneva a suo fratello incarcerato già da anni.

Cade l'unicità del tratto biometrico secondo bertillon.


Esordi delle impronte digitali :
- I primi studi "seri", vengono avviati nel 1892 da Galton. 
Il quale pubblica un libro intitolato finger prints, dove calcola che la probabilità che due individui abbiano le stesse impronte è 1/64 miliardi.
Galton scopre che tutte le impronte possono essere classificate in 4 classi :
- A delta
- Monodelta
- Bidelta
- Composta

La classificazione è ancora oggi fodamentale per gestire grossi archivi di impronte.

- Henry, un ispettore della polizia indiana pubblica nel 1900 il libro "classification and Used of fonger prints".
Il metodo di henry è stato utilizzato come standard fino all'avvento dell'elaboratore elettronico in GB.

A partire dal 1900 tutto il modo utilizza tale metodo come standard.

- Ad oggi in tutti il mondo sono registrati dati biometrici di centinaia di milioni di individui.
In 4 decenni si è passati da :
- 1 metodo impronte
- Sistemi automatici per circa 10 diversi tratti biometrici.

---

Comparazione sistemi e tratti  biometrici
È un problema molto complesso per i seguenti motivi :
- Vi sono molti parametri in giudizio
- I parametri sono difficilmente stimabili, alcuni esempi di parametri :
	- Gradimento degli utenti := parametro importante, misurabile tramite questionari ( domanda di esame)
	- Velocità := numero di confronti che viene eseguito tra il template da verificare e una serie di campioni ( data set).
	- Accuratezza = percentuale con la quale un sistema identifica un utente in maniera corretta.
	- Scalabilità := numero di persone per le quali il sensore è progettato potrebbe aumentare.
	- Interoperabilità := il sistema dovrebbe poter utilizzare diversi tipi di sensori
	- Costo del sistema
	- Usabilità

I tratti biometrici possono essere confrontati per :
- Universalità
- Unicità
- Permanenza
- Collezionabilità
- Performance
- Accettabilità da parte degli utenti
- Facilità di aggiramento ( frode)

Ad esempio :
- Il volto ha un alta universalità ma una bassa unicità ( sistemi non ancora abbastanza evoluti per distinguere due volti), facilmente detezionabile, Bassa permanenza cambia con il tempo.

- Non tutti i tratti vanno bene per fare identificazione e autenticazione nella pratica, nella teoria si :

| Tratto biometrico | Autenticazione | Identificazione |
| ----------------- | -------------- | --------------- |
| Impronta          | SI             | SI              |
| Volto             | Si             | No              |
| Iride             | SI             | SI              |
| Mano              | Si             | No              |
| Voce              | Si             | No              |
| Firma             | Si             | No              |

Il sistema quando deve effettuare l'identificazione con N troppo grandi potrebbe perdere di performance e accuratezza.
Ad oggi solo iride e impronta sono stati usati per identificazione ( 1:N) con N grandi.

Requisiti per il funzionamento 1 : N :
- Accuratezza elevatissime ( tasso errore << 1E-5), l'errore scala con il numero di persone, l'errore sul singolo match deve essere molto basso.
- Template per byte ridotti ( dimensione  < kb), altrimenti con N molto grossi dovrei avere uan base di dati molto grande dove memorizzarli.
- Tempo per singolo confronto molto basso ( t < ms), altrimenti il sistema potrebbe risultare molto lento.

Volto, Mano, Voce e firma vengono solo usati per :
- Autenticazione ( 1:1)
- Identificazione (1;n ) con N molto piccoli


- Altri parametri importanti sono la durabilità del tratto biometrico negli anni e il numero massimo di sample indipendenti :

| Tratto biometrico | Variazione negli anni | Numero massimo di sample indipendenti             |
| ----------------- | --------------------- | ------------------------------------------------- |
| Impronta          | no                    | 10 ho 10 dita, sistemi con più dita sono robusti. |
| Volto             | Si                    | 1 ho un volto solo                                |
| Iride             | SI                    | 2                                                 |
| Mano              | Si                    | 2                                                 |
| Voce              | Si                    | 1                                                 |
| Firma             | Si                    | 1 ( se non si associa un parola chiave)           |

Variazioni del tratto :
Occorre tenere presente se il tratto biometrico cambia nell'arco di una vita o giorno dopo giorno.
Un alta variabilità del tratto biometrico nel tempo produce uan peggiore accuratezza del sistema.

In base al tipo di sistema che si vuole costruire ( sistemi che identificano persone per 7 giorni o anni e anni), si può scegliere un tratto biometrico piuttosto che un altro.
Il progettista deve dunque adeguare la durabilità del tratto biometrico con l'effettivo utilizzo del sistema.

Iride ed impronta hanno ottime caratteristiche di durabilità nel tempo

Purtroppo i tratti che piacciono maggiormente agli utenti sono anche quelli che mostrano maggiore variabilità del tratto biometrico nel tempo.


Sample indipendente:
Non c'è una correlazione statistica ad esempio tra il dito indice e il dito medio pur appartenendo allo stesso individuo.  ( importante per esame) .

Maggiore è il numero di sample indipendenti ( dello stesso tratto) che possiamo usare nello stesso sistema biometrico, maggiore è l'accuratezza rispetto ad usare un sample.

Possiamo di conseguenza controllare 2, 3 N impronte per aumentare l'accuratezza.
Possiamo inoltre registrare impronte diverse per sistemi biometrici diversi.

È possibile avere dei sensori a costo zero, non per tutti i tratti biometrici, ad esempio per la voce ( cellulare)


- Costo del sensore
Ha una grande importanza sulla diffusione e l'impiego del sistema.

Ci possono essere dei sistemi a costo zero ( come ad esempio il microfono del cellulare per rilevare il tratto biometrico della voce), oppure dei sistemi biometrici che costano molto ( riconoscitore di iride).

- Dimensione del sensore
Influenza l possibilità di impiego nei vari sistemi elettronici "embedding"

- Velocità del sistema
Tempo di riferimento = è il tempo misurato in secondi per eseguire completamente un singolo matching. Da questo tempo si arriva a stimare il numero di utenti massimo identificabile/autenticabile in un ora.

Inoltre i sistemi possono funzionare :
- in tempo reale: in cui la velocità e cruciale, es gate aeroportuale
- Off-line: in cui la velocità è importante ma non cruciale, es ricerca delle impronte di un criminale in un archivio

Esempio, Caso dell'aeroporto ( 1 : N ) :
- Abbiamo 2000 iridi registrate nel sistema come "persone indesiderate" ( N = 2000)
- Vogliamo che la persona venga identificata negativamente in 2 secondi.
- Il tempo per eseguire un singolo matching deve essere minore di 1 ms, il qual è davvero poco

- Interoperabilità
Si tratta della capacità di un sistema biometrico di funzionare anche con sample biometrici acquisiti con sensori di diverso tipo usando lo stesso tratto biometrico.
L'argomento della interoperabilità diventerà sempre più importante visto che il tipo di sensori è destinato ad aumentare nel tempo. (esame)

Ad esempio il sistema FBI IAFIS, ovvero un db di template di impronte, viene alimentato con impronte digitale proveniente da vari sensori ( online, inchiostro scannerizzate)

- Scalabilità
Si tratta di stabilire come viene influenzata l'accuratezza e la velocità del sistema rispetto al numero di campioni contenuti nel sistema.
Possono essere generati dei tratti biometrici sintetici per vedere come si comporta il sistema.

- Percezione degli Utenti
L'uso delle tecnologie biometriche per l'identificazione/autenticazione viene spesso percepito in modo eterogeno, ovvero in modo duplice.

- Vantaggi percepiti dagli utenti :
	- Non devo avere chiavi o ricordare codici ( Vero)
		I tratti biometrici tuttavia,  non possono essere cambiati come una password, occorre costudirli.
	- Sarà più difficile clonare o rubarmi i soldi con il mio bancomat  (Parzialmente vero)
		- Esistono modi per frodare un sistema biometrico, ma sono molto complessi
		- La tecnologia anti-spoofing procede di pari passo con quella di spoofing.
	
	- Funzionerà contro il terrorismo (parzialmente vero)
		- Sarà più difficile usare gli alias, documenti falsi o clonare carte
		- Il problema delle identità multiple viene azzerato
		- Rimane il problema dell'anello debole della catana di identificazione : la fonte

- Svantaggi :
- Le impronte saranno schedate come quelle dei criminali  (parzialmente vero)
	- Le tecnologie sono simili o uguali  ( interscambiabili) a quelle impiegate dalla polizia, tutta via cambiano il DB dove sono memorizzati i template  e il loro impiego. 
- Tramite la biometria, gli utenti si sentono spiati, tracciamento dei loro movimenti, dove vado e cosa compro. ( già vero oggi )
	- Questo accade già con ausili come il telepass, i pagamenti online di biglietti con carta di credito e ogni volta che usiamo internet per acquistare qualcosa.
	- L'utilizzo della biometria allunga semplicemente il periodo di tempo per il quale un movimento è tracciabile


- Anello debole della catena di identificazione ( esame)
Il problema è la fonte, ovvero come nasce un documento biometrico, infatti un documento biometrico nasce da altri documenti tradizionali.

Ad esempio per il passaporto biometrico servono :
- 2 foto formato tessera, di cui una autenticata
- 1 marca da bollo
- 1 attestato di versamento
- Un documento di riconoscimento valido
- A questo punto viene rilevata l'impronta e creato il documento.

Il problema principale è quindi che il documento biometrico nasce da un documento di identificazione cartaceo, il quale potrebbe essere fasullo.

Problematiche che si possono verificare :
- Ipotesi a bassa probabilità :
Se si riuscisse a corrompere/costringere un semplice funzionario, un nuovo terrorista XYZ potrebbe avere un perfetto passaporto biometrico con nome mario rossi.

- Ipotesi a media probabilità
	- Supponiamo che si presenti il terrorista XYZ dalle autorità italiane nella città dove risiede dopo essere immigrato dallo stato ABC
	- Il sig XYZ porta tutti i documenti rilasciati dallo stato ABC i quali attestano che esso sia mario rossi.
	- Le autorità producono quindi il passaporto biometrico con nome mario rossi associato a xyz.

- Differenza sample vs template ( esame)
Non esiste una tecnologia meglio di un'altra.
SAMPLE := si tratta di un immagine, foto di un occhio, foto di un impronta.
- Vantaggi, a differenza dei template può essere nuovamente :
	- Filtrato
	- Analizzato
	- Permette cambi tecnologici

- Svantaggi :
	- Occupa più spazio
	- Dato utile per attacchi con fake
	- Allunga la vita del tratto biometrico
	- Lede la privacy

Template := stringa di bit che identifica univocamente una serie di caratteristiche di un tratto biometrico opportunamente codificate
- Vantaggi :
	- Minore elaborazione in verifica
	- Minore occupazione di memoria e banda in trasmissione
	- Protegge meglio la privacy, ha una durata temporale minore.

- Template :
	- Legato alla tecnologia che lo ha generato
	- Difficilmente migliorabile
	- Esistono molti studi che dimostrano che è possibile da un template ricostruire una copia molto simile al sample generato.


- Problema della proscription
Quando un dato biometrico è inviato ad un dato sistema, l'informazione contenuta non dovrebbe  essere usata per altri scopi se non quello dell'uso richiesto dell'utente

In ogni sistema informativo basato su rete è difficile assicurare che il dato inviato verrà usati per gli scopi richiesti. Non è solo un problema della biometria, tutta via quest'ultima prova che la richiesta l'ha fatta un particolare utente ( difficile da ripudiare)

Di conseguenza devono essere stabilite delle politiche di privacy .

- Variazioni del tratto e privacy
Usare un tratto biometrico che varia molto nel tempo tende a produrre molti falsi negativi, il sistema dice che non sono io. Tale errore fa arrabbiare un cliente che ha pagato per il servizio.

Ma allora perche non si utilizzano sempre l'impronta e l'iride visto che hanno tassi di errore tra i più bassi ?
- Costo del sistema
- È corretto adattare l'invasività del tratto e l'accettazione degli utenti con il grado di sicurezza richiesto (esame )
- Usare un tratto che varia nel tempo può proteggere dall'effetto "schedatura"

Un template di una impronta o un iride memorizzato in un sistema biometrico può provare che un utente è stato in un certo posto per decenni, con errori trascurabili.

Un sistema biometrico basato sulla voce  e legato ad una parola chiave riuscirà ad identificarvi con elevata accuratezza solo se voi vorrete ripronunciare la parola chiave

Per una centrale nucleare o un aeroporto ha senso usare il primo tipo di biometria, per entrare comodamente a DineyWorld sarebbe meglio usare il secondo tipo


Aspetti generali e regolamentazione
La legge in vigore attualmente sui dati biometrici è :
25/05/2018
GDPR

- Decalogo del garante sulla biometria (2006). Il decalogo è una guida operativa per chi progetta e costruisce sistemi per la rilevazione di dati corporei.
1. Affidabilità del sistema := Deve essere indicata l'accuratezza del sistema, valutata da tecnici indipendenti.
2. Informativa chiara := Deve essere lasciata la libertà di aderire all'utente, nel caso devono essere previste delle tecniche alternative alla biometria.
3. Liceità := l'uso dei dati biometrici  ( se previsto) deve essere circoscritto ( impronta di un solo dito anziché più impronte).
4. Deroga motivata := uso controllato del sistema in speciali casistiche e non uso generalizzato o incontrollato.
5. Delimitata memorizzazione (non centralizzazione)
6. Temporanea conservazione := periodo di tempo di conservazione dei template limitato.
7. Scrupolose misure di sicurezza
8. Piena ed immediata conoscibilità dei dati biometrici da parte dell'interessato
9. Rispetto rigoroso delle norme e obblighi di verifica preliminare e notifica del Garante
10. Disattivazione automatica, immediata e certa di funzioni di smart card o altre analoghe in caso di smarrimento o furto

- Il 12 novembre 2014 il garante privacy ha adottato un provvedimento generale in tema di biometria, fissa un quadro unitario di misure e accorgimenti.
La definizione che il garante della privacy assegna ai dati biometrici è la seguente :
_proprietà biologiche, aspetti comportamentali, caratteristiche fisiologiche, tratti biologici o azioni ripetibili laddove tali caratteristiche e/o azioni sono tanto proprie di un certo individuo quanto misurabili, anche se i metodi usati nella pratica per misurarli tecnicamente comportano un certo grado di probabilità_

Il quadro normativo biometria, inoltre afferma che nel caso in cui un sistema sia abilitato al rilevamento di dati biometrici di un certo interessato senza la sua cooperazione, occorre informare gli interessati, anche attraverso un apposita segnaletica (solo in aree pubbliche) , dando loro la possibilità di accedere o meno alla zona sottoposta da controlli biometrici.

Qualora il dato biometrico sia registrato in un dispositivo ( nell'esclusiva disponibilità dell'interessato) l'informativa dovrà fornire adeguate istruzioni sulla sua corretta custodia e sugli adempimenti .

05 2014: L'Autorità ha individuato specifici casi in cui non sarà più necessario effettuare un interpello preventivo ( verifica preliminare ) per l'adozione di tecnologie biometriche:
- Autenticazione informatica
- Controllo di accesso fisico ad aree “sensibili” dei soggetti addetti e utilizzo di apparati e macchinari pericolosi
- Sottoscrizione di documenti informatici con tecniche biometriche basate sul rilevamento della dinamica di apposizione della firma.
- Uso delle impronte digitali o della topografia della mano a scopi facilitativi

---

Aspetti di architettura dei sistemi biometrici
Struttura di un sistema biometrico :
Viene divisa in due fasi :
- Enrollment
- Verifica

- Struttura Generale  della parte di enrollment :
	- L'impronta viene acquisita attraverso un opportuno sensore
	- Successivamente viene effettuato un controllo di qualità ( per non inserire nel database template di scarsa qualità)
	- Successivamente vengono estratte le feature, decodificate ottenendo così il template
	- Il pin o il nome ci permette di associarlo ad un particolare template che stiamo memorizzando. Permettendoci così di effettuare sia l'autenticazione che l'identificazione
![[Pasted image 20231106093952.png]]
- Struttura generale della parte di verification con DB:
	- Visto che ho a disposizione un nome fornito dall'utente, tramite una apposita query sul db posso andare ad estrarre solamente il template associato a quel nome e confrontarlo con quello acquisito.
	- Eseguo un operazione di matching, se il matching è superiore ad una cera soglia, l'utente è abilitato ad entrare nel sistema

![[Pasted image 20231106094018.png]]

- Struttura per identification con DB :
Lo schema segue quello precedente. Tutta via non posso andare a selezionare un template specifico dal db, ma dovrò andare a confrontare l'impronta acquisita con N template.

- Struttura enrolment e verification con un documento biometrico :
I dati non vengono più salvati su DB ma su il documento biometrico.
La verifica avviene con solo un template ( quello impresso sul documento), il dove avviene questo matching caratterizza il tipo di sistema.

- Un sistema biometrico multimodale utilizza più di un tratto biometrico, sia fisiologico che comportamentale, in una qualsiasi fase ( enrollment, verification, identification)  (esame)
Parto dallo schema generale di identificazione di un sistema mono-modale e la copio in base a quanti tratti biometrici il mio sistema multimodale utilizza.

- Sistemi biometrici distribuiti
Il termine distribuito si riferisce ad un sistema biometrico quando i moduli componenti sono separati e collegati in rete.

I sistemi di autenticazione non ha senso che siano distribuiti. Tutta via è il contrario per i sistemi di identificazione  (esame)  :
- Sistema di identificazione in aeroporto
- Sistema di controllo delle frontiere

Solitamente è il modulo dei Db dei template che viene dislocato rispetto ai terminali , per due principali ragioni :
- Di sicurezza  ( fisica e logica), bisogna garantire la protezione dei dati sensibili.
- Per collegare DB distribuiti su una LAN/WAN

Modello di Mainsfield e Wayman
![[Pasted image 20231106094126.png]]
Si tratta di un modello funzionale, l'impronta registrata da un sensore può seguire due percorsi :
- Se siamo nella fase di enrollment, essa verrà registrata nel data storage
- Altrimenti verrà eseguito un matching.
	Possiamo osservare come nella decisione di ammettere l'utente nel sistema o meno, non viene utilizzato solo il matching score, ma viene utilizzato anche il quality score (qualità del template acquisito) , il quale ci permette di dare un peso al matching score di un determinato tratto biometrico.


- Sistemi biometrici on card
Il termine un card si riferisce al fatto che il template biometrico risiede su una smart card.

La smart card non effettua il matching ( potenza computazionale bassa), viene effettuato su un pc a cui è collegato il sensore di acquisizione.
Non possiede un sensore di acquisizione ( si una un sistema esterno).

Negli anni, tutta via si sono sviluppate delle card dotate sia di sensore fino ad arrivare a delle matching on card ( con degli algoritmi semplificati) . Diventa quandi difficile frodare il sistema in quanto è tutti locale.

Il matching sta diventando possibile farlo on card ( esame) 
Oggi inoltre esistono delle tecnologie che permettono di eseguire il matching on sensor :
Arrivano sul mercato dei nuovi sensori con molte funzionalità utili per lo sviluppo del sistema. Synpatics SentryPoint :
- Encryption
- Match - in - sensor
- Anti spoof tecnology ( attacco più difficile in quanto i moduli del sistema non sono dislocati e inoltre il sensore offre tutti i moduli crittografici per interagire con altre tecnologie)

Domande esame riguardanti :
- Sistema biometrico generale nelle fasi di
	- Enrollment
	- Verification
	- Identification
- Sistema biometrico multimodale
- Sistema distribuito
- Sistema biometrico in card



Aspetti analitici di un sistema biometrico
Variabilità temporale del tratto  :
- l'impronta non si degrada nel breve periodo e nel lungo periodo, il suo pattern rimane visibile. 
	Le persone di età giovane in generale hanno un ottima qualità dell'impronta ( ovviamente ci sono degli outlier, ad esempio persone che fanno particolari lavori) , le persone anziane in generale hanno una qualità dell'impronta più bassa.
- Il volto rimane "simile" entro un paio danni. Abbiamo una degradazione molto alta se parliamo di decenni, degradazione dei tratti biometrici. Tutta via tale degradazione consente di mantenere una maggiore privacy.

Abbiamo delle problematiche sia intraclasse che inter classe, esse devono essere risolte dai sistemi biometrici

- Variabilità intra-classe ( esame)
Intra-calsse = stesso individuo

Si intende la variazioni dei sample e delle feature ( caratteristiche) dello stesso individuo tra acquisizioni effettuare in istanti di tempo diversi.
Tale variabilità è dovuta a :
- Effetti casuali ( rumore del dispositivo)
- Variazioni dello sfondo
- Variazioni del tratto biometrico ( invecchiamento, posizione, usura)
- Parziali occlusioni ( mascherine, capelli, sopracciglia)


- Similitudine interclasse ( esame)
Inter classe = variabilità tra persone diverse.

Abbiamo dunque persone diverse che si assomigliano. Si tratta di una particolare vicinanza dei sample o delle feature acquisiti da individui diversi.


Regole generali di progettazione dei sistemi biometrici
Per ognuna delle fasi nello schema generale di un sistema possiamo applicare delle particolari tecniche, le fasi da analizzare sono le seguenti :

- Acquisizione del tratto
- Rappresentazione
	- Del sample
	- Estrazione delle caratteristiche
	- Del template
- Matching
- Ricerca, organizzazione e scalabilità

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

---

Occupiamoci ora di migliorare la fase di Rappresentazione :
- Rappresentazione del sample
- Estrazione delle caratteristiche
- Del template

Cos'è la rappresentazione  := Una acquisizione di un sistema biometrico ( non elaborata) è tipicamente :
- Non invariante ( rispetto al momento di acquisizione), il sistema deve trovare la parte del tratto che non varia nel tempo e salvarsi quelle informazioni.
- Ed è decisamente non discriminatoria ( sono tutte diverse), le informazioni estratte devono essere univoche.

In un sistema biometrico occorre studiare come meglio rappresentare l'informazione per rispondere alla domanda :

"quale rappresentazione "machine-readable" ( automatica) cattura completamente l'informazione invariante e discriminatoria della misura in ingresso "

Il problema della rappresentazione, consiste nel determinare uno spazio di misura ( fetuare space) che sia :
- Invariante ( meno variante) rispetto ad acquisizioni dello stesso individuo
- Che si differenzi massimamente per le acquisizioni provenienti da individui diversi.
In altre parole si può affermare che la rappresentazione deve fornire una :
- Alta variabilità interclasse
- Bassa variabilità intra-classe

![[Pasted image 20231106094844.png]]
(esame)

La fase di rappresentazione è uno dei cardini della progettazione di un sistema biometrico, influenza direttamente tutte le fasi successive della progettazione.
Le problematiche inerenti al problema della rappresentazione nel sistema biometrico per la parte di estrazione delle caratteristiche e della creazione del template impattano sul modulo evidenziato ( feature extration )  presente sia in fase di enrollment che di verification/identification

L'affidabilità della rappresentazione dipende dal :
- Tratto biometrico := Tratti biometrici "semplici" ( basso contenuto informativo, come la firma) produrranno rappresentazioni meno affidabili dei tratti "complessi" come ad esempio la firma.
- Dominio applicativo del sistema := La rappresentazione diventa meno affidabile se :
	- All'aumentare degli individui da confrontare fra loro ( aumento dei record del db). Diminuisce la varianza inter-classe
	- In caso di sensori rumorosi, soggetti non collaborativi.

Rappresentazione del sample :
Si riferisce alla caratteristiche tecniche del processo di acquisizione e memorizzazione ( anche temporanea) del sample, le quali vanno a generare il template. Ovviamente tali tecniche di memorizzazione variano a seconda del tipo di tratto biometrico :
- Firma online = intervallo di campionamento, numero di bit del dato, numero degli assi rillevate
- Impronta digitale = metodo di acquisizione, risoluzione del dispositivo, numero di bit dei toni di grigio.

Spesso si riferisci a questi dati con RAW data

Una volta ottenuti i dati raw, provenienti dalle misurazioni (sample) occorre ora estrarne la rappresentazione nello spazio delle caratteristiche.
Esistono sia sistemi manuali che automatici per l'estrazione delle caratteristiche.
I sistemi completamente automatici non seguono quasi mai un approccio simile, lo spazio delle caratteristiche di un sistema automatico tende ad essere diverso da quello di un sistema manuale. Inoltre ha una struttura organizzata in moduli software.

![[Pasted image 20231106094936.png]]

Questo non è mai un problema semplice specialmente con dati rumorosi.


Migliorare la fase di matching 
Le problematiche inerenti al problema della rappresentazione nel sistema biometrico per la parte di matching impattano solamente il modulo di matching, il quale è presente solamente nelle fasi di verification e identification.

Dobbiamo andare a definire una metrica nello spazio delle feature, la quale permette di misurare la distanza tra due template per determinare se essi siano simili o meno.

Esempio di matching fra impronte, input e templare :
- Template in ingresso := in ingresso vengono passata le coordinate minuitae e le loro angolazioni
- Vengono eseguite delle rototraslazioni per allineare le 2 mappe attorno ad una minutia.
- Vengono individuate le coppie di minutae corrispondenti nelle 2 mappe
- Calcolo delle distanze e dell'indice di matching

Tutta le impronte di uno stesso individuo potrebbero essere raccolte con deformazioni ( troppa pressione sul sensore ) le distanze relative alle minutiae cambiano e quindi diventa difficile avere un buon valore di matching. Possiamo dunque adottare delle contro misure :
- Prendere provvedimenti per evitare che l'utente deformi l'impronta durante la scansione
- Inserire nell'algoritmo di matching anche un modello elastico di deformazione, tutta via aumenta la similitudine intraclasse ma tende a diminuire la distanza interclasse.

Domande esame
- Come il problema della rappresentazione della informazione in un sistema biometrico consista nello stabilire quale rappresentazione “machine readable” catturi completamente l’informazione invariante e discriminatoria della misura in ingresso
- Come questo possa essere visto in termini di distanza interclasse ed intraclasse nello spazio delle feature
- Soluzioni al problema della rappresentazione dei sistemi biometrici
	- Del sample
	- Della estrazione delle feature
	- Del template
- Come il modulo di matching implementi una metrica nello spazio delle feature


Migliorare la ricerca, organizzazione e scalabilità del DB
L'obbiettivo principale è quello di migliorare la scalabilità. Dobbiamo garantire che i sistemi che devono gestire una grande quantità di identità, dovrebbero essere in grado di operare efficacemente quando il numero di utenti registrati nel DB aumenta.

Si richiede inoltre che il tasso di peggioramento delle prestazioni sia minore del tasso dei nuovi utenti immessi nel sistema.

L'introduzione della biometria in un sistema di identificazione di grandi dimensione porta ad una serie di vantaggi :
- Le tecnologie biometriche non soffrono come quelle tradizionali del problema della produzione e del rinnovo dei documenti di identità.
	- Rinnovo della care di identità del passaporto per scadenza o smarrimento
- Le tecnologie biometriche iniziano ad essere competitive in termini di costo e mantenimento.
	- Un buon lettore biometrico funziona per anni, non ha bisogno di particolari aggiornamenti tecnologici.

L'obiettivo di gestire efficacemente la complessità delle ricerche all'incremento del numero di template nel DB del sistema può essere raggiunto solo con una attenta organizzazione del DB, un DB organizzato permette di non confrontare un template in ingresso con tutti i template nel DB ma solo con quelli contenuti in una partizione.

Ad esempio :
Le impronte possono essere classificare come "arch", "loop" ecc.. Se il sistema usa due impronte, allora i matching verranno effettuati solo con la porzione di database contenente template di individui con le due impronte dello stesso tipo di quelle in ingresso.

Ad esempio per un sistema basato su due impronte e capace di calssificarle in arch o loop avremmo 4 partizioni o bin possibili. 

![[Pasted image 20231106095131.png]]

Attualmente i sistemi di grandi dimensione funzionanti su due impronte riescono a funzionare correttamente con dei Penetration Rate del 10%.

Per giovare delle partizioni del DB occorre disporre di un algoritmo automatico molto robusto per la classificazione dei template. Quando il DB viene creato, i template vengono disposti nelle partizioni ( bins)

Il numero di bins ( partizioni)  ottimale  può essere calcolato nel seguente modo :

Se ho N  impronte disponibili  ( indice, medio, …) tutte divisibili in N_tipi ( arch,loop,…) allora il numero migliore di bin è dato da: $N_{bin} = N_{tipo}^{NumeroImpronte}$

Ad esempio :
Se abbiamo due impronte ( N impronte = 2 )
Con 3 tipi possibili in cui un impronta viene classificata ( N_tipi = 3 )

Il numero di bins ottimale è $N_{bin} = 3^2 = 9$


Binding error :
I problemi nascono quando un individuo presenta i propri tratti biometrici al sistema e l'algoritmo di classificazione del tratto sbaglia il bin ( binding error).
Se l'individuo era registrato nel DB, con alta probabilità non si avrà un match in quanto i template che matchano sono registrati da un bin diverso da quello scandito.

Penetration rate := percentuale ( spesso espressa con un rapporto) con cui un sistema è in grado di identificare correttamente gli utenti all'interno del DB.
La frazione media di template che occorre controllare nel DB per tutti i possibili input, tenendo conto che la ricerca continui nella partizione anche se si verifica un match.
Tiene conto della distribuzione degli individui.

(esame) N:B =  Avere N bin non porta ad avere un penetration rate del 100/N. Questo accade perché i bin non contengono necessariamente un numero di individui uguali.  La distribuzione degli individui nei bin dipende dalla distribuzione statistica della popolazione che quasi mai è uniforme.

È dimostrato come si possa arrivare ad un tasso di errore del 5-10% in un db di medie dimensioni attuando una classificazione di Henry con un sistema automatico ( 5 classi). Gli errori si moltiplicano se si usano N impronte.

Notare cosa succede abbassando il numero di classi :
- P.R. sale → si abbassa la qualità del P.R. ottenibile (non buono)
- Si abbassa l’errore di classificazione (buono)

Domande esame:
- Scalabilità ed organizzazione della ricerca in un DB biometrico
- Il sistema di partizione (binning) del DB mediante classificazione del tratto biometrico
- Le differenze fra il Penetration Rate ed il Binning rate


Quanto sbaglia un sistema biometrico ?
La domanda che ci andiamo a porre è qual è il tasso di errore di verifica/identificazione

Descrivere il funzionamento di un sistema con un solo tasso di errore è quasi sempre sbagliato.

La soglia di un sistema biometrico influisce su come il sistema biometrico funziona e lavora.


Genuini ed Impostori
Si impiegano i termini :
- Genuino  = per indicare un individuo che accede al sistema e ha titolo per farlo.
- Impostore = per chi prova ad accedere senza averne il titolo ( zero effort) .

la soluzione del problema è diversa a seconda che il sistema funzioni in verification o identification  :

- Caso della verifica
Dobbiamo verificare se l'utente è chi dice di essere, si tratta di un problema di classificazione binaria.

Dati in ingresso (query) :
-  un insieme di caratteristiche Xq
- dichiarazione di identità I.

Occore determinare se ( I, Xq) appartengono a w1 o w2, dove :
- W1 indica che la richiesta è vera ( utente genuino)
- W2 indica che la richiesta è falsa ( un impostore)

Le caratteristiche Xq vengono controllate con le caratteristiche XI ( il template memorizzato nel sistema associato alla identità I)

Regole di decisione per la verifica :
Si tratta di una comparazione con soglia
$$ (I, X_q) \in {\begin{cases} w_1 \text{ SE }S(X_q, X_i)>=T \\ w_2 \text{ ALTRIMENTI} \end{cases}}$$
- S è la funzione che misura la similitudine tra XQ ( ingresso) e XI template
- T è la soglia prefissata

S(Xq, Xi ) Si chiama similarity score o match score
L'impronta inserita viene confrontata con un solo template nel db ( 1:1).

- Caso dell'identificazione
Nel caso dell'identificazione dobbiamo controllare se i dati biometrici inseriti dall'utente corrispondono ad un insieme di identità registrate, può essere formalizzato nel seguente modo :

Dati in ingresso : un insieme di caratteristiche Xq (query)

L'obbiettivo è quello di determinare l'identità Ik con k appartenente all'insieme {1,2,3,…,M,M+1} dove I1, I2, Im  sono le M identità memorizzate nel sistema e Im+1 rappresenta il caso di reiezione ( nessuna delle M identità registrare è simile all'ingresso). Il caso di reiezione è necessario in quanto altrimenti andrei a selezionare l'identità che assomiglia di più all'ingresso autorizzando cosi un impostore.

I dati in ingresso vengono confrontati con più templare (1:N) e non più solo con uno come prima

Regole di decisione della identificazione:   
Si tratta di M comparazioni con soglia
$$(X_q) \in {\begin{cases} I_k \text{ SE } k=argmax S(X_q, X_{ik} \text{ and } S(X_q, X_{ik}) >=T) \\
I_{M+1} \text{ altrimenti}\end{cases}}$$
- Xik è il templare corrispondente alla identità Ik
- T è la soglia prefissata

In alcuni casi ci si riferisce ad una misura della distanza fra Xq e Xi. Una grande distanza fra i vettori di feature porta a un basso match score.


N template provenienti dalla stessa persona ed acquisiti in tempi diversi non sono mai uguali ( esame)
Esiste sempre una distanza nello spazio delle feature che separa i template anche della stessa persona, Questo è dovuto a fattori come :
- Rumore di acquisizione
- Diversa posa del soggetto
- Diversa illuminazione o sfondo
- Condizione ambientali

Questo porta al fatto che la soglia T non può essere arbitrariamente abbassata, altrimenti nessuno sarà identificato (ad esempio se impostiamo T=0) ( esame).
Se si riscontrasse uan distanza nulla fra Xq e Xi S(Xq e XI) = T, probabilmente saremmo di fronte ad un replay_attack = copia illecita di un template memorizzato che viene riproposto in ingresso per frodare il sistema.

Chiamo con :

- Genuine score = quando si confrontano le distanze fra template dello stesso individuo
- Impostor score  = quando si confrontano le distanze fra template di individui diversi

Possiamo avere inoltre due casi di errori possibili :  (esame)
- Il ladro entra in casa perché il sistema biometrico lo ha scambiato per un utente autorizzato ( False Matching, errore di tipo 2) . Questo caso si verifica quando l'imposto score è maggiore della soglia T impostata
- Noi non entriamo in casa perché il sistema biometrico ritiene che il nostro template non assomigli abbastanza a quello registrato ( False non - Matching, Errore di tipo 1) .Corrisponde al caso in cui il genuine score è minore della soglia T impostata.


FM RATE, FNM RATE
Supponiamo di poter variare la soglia s del sistema e fissarla ad un valore T in mezzo fra il picco degli impostori e quello dei genuini.
![[Pasted image 20231106100430.png]]
- Possiamo notare che un certo gruppo di persone dei genuini non sarà riconosciuto dal sistema, in quanto sono sotto alla soglia prestabilità. Daranno quindi luogo ad errori di False non matching.

False not matching raiting con soglia T -> FNMR(T) = FNM(T) / totale genuini 

Il numero totale di persone appartenente al gruppo dei genuini ( sotto la soglia T) FNR, deve essere calcolato con un integrale della porzione di curva dei genuini fino alla soglia T

- Al contrario parte degli impostori saranno riconosciuti dal sistema, in quanto hanno un valore di matching sopra la soglia. Daranno vita ad errori di false match

False matching raiting con soglia T -> FMR(T) = FM(T) / totale impostori 

Il funzionamento di un sistema biometrico dal punto di vista degli errori commessi è principalmente descritto dai tassi FMR(T) e FNMR(T) descritti per tutti i valori della soglia.  Tali valori inoltre sono in funzione della soglia scelta T.

L'andamento del sistema può essere descritto dalla funzione DET ( decision error Tradeoff), mostra come variano i valori di FNMR ( y)  e FMR (x) al variare del parametro T.  Esprime quanti genuini non sono riusciti ad entrare nel sistema.
La curva Det non rappresenta nessuna distribuzione.

È possibile sapere a priori i punti dove la curva DET passerà ( esame)
Se faccio una soglia che è +infinto, nessun impostore passerà come nessun genuino ( la curva passa da +infinito e -infinito 1 0 e 0 1 ) .
La soglia adatta è quindi quella che viene attraversata dalla bisettrice. Introduce L'EER ( Equal error rate). È l'unico numero singolo che può riassumere il funzionamento del sistema FNMR = FMR. 

![[Pasted image 20231106100529.png]]

Abbiamo diverse zone di funzionamento in base alla realtà che vogliamo modellare :

| FNMR alto  | FMR basissimo quasi zero | Alto livello di sicurezza   |
| ---------- | ------------------------ | --------------------------- |
| FNMR basso | FMR alto                 | Applicazioni forensi        |
| Bisettrice |                          | Applicazioni civili normali |

La Curva ROC è l'analogo di DET. ROC = 1 - DET
ROC Esprime quanti genuini sono riusciti correttamente ad entrare. 
![[Pasted image 20231106100609.png]]

CMC ( Cumulative Match Characteristics )
Nel contesto della identificazione si può valutare il grafico CMC.
Supponiamo di cercare un impronta latente, chiediamo al sistema biometrico di scegliere le 10 impronte più vicine a quella cercata, qual è la probabilità che ci sia dentro al pool quella cercata.

La curva rappresenta la probabilità di identificare una persona in base al pool di impronte che abbiamo selezionato. Le impronte nel pool sono ordinate in base al match score.
- N = numero persone del DB
- Per ogni individuo k ordino gli R ( = Rank) individui più simili a k.
- Conto le volte che appare k era negli R trovati per tutti k
![[Pasted image 20231106100640.png]]
Caratterizzazione degli utenti the Doddington zoo
- SHHEPS ( percore) = Utenti con features molto distintive e bassa variabilità intraclasse. Avranno bassi FMR e FNMR.
- GOATS (capre) = Utenti con alta variabilità intraclasse. Tendono ad avere molti False Reject.
- LAMBS ( agnelli) := Utenti con features che si sovrappongono estesamente con quelli degli altri, hanno una bassa distanze interclasse. Un agnello entra al posto di una percora. Hanno un false Accept Rate alto.
- WOLVES (Lupi): Individui capaci di manipolare il tratto biometrico (i tratti compartamentali di solito) per impersonare un utente legittimato. Un lupo entra al posto di una pecora.
	Aumentano il False Accept Rate


Modelli statistici in un sistema biometrico
Qual è il modello statistico migliore per caratterizzare un sistema biometrico :
- Sistema di lancio = Abbiamo un modello aleatorio. Probabilità che esca il numero 6 (Out=6) = 0.16
- Sistema di lancio truccato = Abbiamo un modello non più aleatorio ma deterministico, la probabilità che esca 6 è più alta. P(out = 6) = 0.67
- Sistema classificazione generale = P(sbagliata classificazione genere)  =0.2.
	Controllo se il classificatore assegna una label sbagliata ad un immagine in ingresso.
	La struttura statistica è la stessa nei casi precedenti. 

Tutti questi modelli rientrano in una categoria più grande la quale prende il nome di esperimenti/prove di Bernoulli :
- Ad ogni singola prova si hanno due esiti possibili ( binari), 1 successo, 0 insuccesso
- La probabilità P dell'evento successo è costante, la probabilità di successo non cambia nel temo.
- I risultati delle prove sono indipendenti. Non riuso lo stesso sample nelle varie prove.

Il sistema biometrico in autenticazione mostra un tasso di errore stimabile e fissato P.
P = è l'errore del sistema biometrico false true match + ture false match.

L'evento che il SB sbagli un autenticazione è un esperimento/ prova di Bernoulli.
Un SB che viene usato in identificazione (1:N) si può modellizzare come N prove di Bernoulli, ovvero un processo di Bernoulli : ( per determinare in generale l'errore del SB)

Variabile Aleatoria X può valere :

- X = 1 ( successo) oppure X = 0 (fallimento) .
- Probabilità di successo è p, probabilità di fallimento è q = 1-p.
- Per noi X = 1 è un errore sul singolo test del Sistema Biometrico.

Il numero di Errori del Sistema biometrico dopo N prove è dato dalla variabile aleatoria Sn : 
$$S_n = X_1 + X_2 + ...+ X_n$$
La probabilità di avere k errori su n prove è :
$$P(S_n = K) = (\begin{array}{c} n \\ k \end{array}) * p^k *q^{(n-k)}$$

La probabilità È in funzione del numero di prove e di P ( probabilità di errore sulla singola prova)

Es:
Se il sistema ha
p =1e-2, la Probabilità di avere 1 errore su 1000 si trova applicando la formula con n=1000, k=1

Che differenza c'è tra la roulette russa e un sitema biometrico ? Nelal roulete russa più aumento il numero di tentativi più ho probabilità di sbagliare, stessa cosa in un sistema biometrico, la probabilità di errore viene moltiplicata per il numero di tentativi.
Roulete russa = sistemi biometrici .

Regole per definire correttamente il tasso di errore P :  (esame)
- Regola dei 3
Qual è il tasso di errore più basso p che può essere stimato con un esperimento di comparazione di N campioni indipendenti.

Se abbiamo un sistema che commette zero errori su N prove, non dobbiamo pensare di avere un sistema con p = 0, ma con il 95 % di confidenza, ovvero p  circa 3/N.
Il 95 % delle volte che faremo l'esperimento l'errore sta nell'intervallo tra 0 e 3/n. 
Altrimenti le nozioni statistiche prima non potrebbero essere vere.

Esempio ;
Se faccio 300 prove con campioni indipendenti e ho zero errori, allora posso dire che con una confidenza del 95% il mio sistema ha un tasso di errore stimato del p = 3/N ->  3/300 = 0,01 * 100 = 1,0 %

- Estensione della regola dei 3
![[Pasted image 20231106101456.png]]
Se ho 1000 persone e ho sbagliato 5 volte, non vado a dire che con il 95 % della confidenza p è circa 5/n ma che p è compreso tra 5/n e 10/n.

- Da verification a identification
Quanto aumentano gli errori nel mio sistema se uso un sistema di verifica (FNMR, FMR) in modalità identificazione (FMR n , FNMR n) (esame)

- FNMR n = FNMR  ( i tassi di errori per i genuini no cambia)
Lavorare in autenticazione o identificazione per un utente genuino ( registrato nel sistema) non cambia.

- FMR n = 1 - (1-FMR)^ N   (con N numero campioni confrontati)
Ovvero = 1 - ( la probabilità che non ci sia un False match su tutti i campioni confrontati con N)

N.b ) con FMR piccolo, l'espressione diventa FMR n = N * FMR
Ovvero l'errore dei false match aumenta linearmente con le dimensioni dei DB. L'aumento di errore sugli impostori aumenta linearmente in base al numero di campioni registrati nel DB.

L'errore degli impostori FMR viene gonfiato di molto in identificazione

- La regola dei 30 (esame)
Quante persone mi servono per dire con uan certa confidenza che l'errore è sterro. La regola dei 30 è usata per determinare la larghezza del campione biometrico :
Per essere sicuro  con un intervallo di confidenza del 90 % che il tasso di errore vero sia tra il +- 30% del tatto di errore osservato ci devono essere almeno 30 errori.

Ad esempio :
Se abbiamo 30 errori in 3000 comparazioni di genuini indipendenti, possiamo dire ( con intervallo di confidenza del 90%) che l'errore vero sta tra 0.7% e 1.3%

30/3000 = 0,01 * 100 = 1,0
Il tasso di errore vero sta sul 30% di 1% (1/30)  ovvero +0.3 - 0.7.

Simulazione :
- Qual è la formulazione esatta del problema della rappresentazione nei sitemi biometrici  ?
 il problema consiste nell'individuare quale rappresentazione machine readable cattura completamente l'informazione invariante e discriminatoria della misura in ingresso.
- La progettazione della rappresentazione dei dati nel sistema biometrico si considera completa quando si è decisa :
	- La rappresentazione dei sample
	- Algoritmi di estrazione delle feature
	- Rappresentazione del template
- La gestione di DB biometrici di grandi dimensione può essere migliorata se :
	- Tutte le precedenti
- Definizione di penetration rate
	- La frazione media di template che occorre controllare nel DB per tutti i possibili input, tenendo conto che la ricerca si intterrompe al primo match trovato nella partizione.
- In un sistema biometrico funzionate con 2 impronte digitali e dotato di un sistema di classificazione in 3 classi con un tasso di errore del 7% qual è la probabilità del binding error ?
	- Nel 7% includiamo già la probabilità di errore considerando tutte e 3 le classi, di conseguenza tale dato non ci serve.
		La provabilità di errori aumenta linearmente con il numero N di campioni ( in quanto gli N sono indipendenti)
		7 * 2 = 14 %
- Il tasso di errore FMR per una data soglia T di decisione è un ottimo indicatore delle performance del sistema biometrico per uan specifica applicazione ?
	- Falso, in generare solo un indicatore di errore non è sufficiente. Sempre FMR E FNMR.
- Quale curva si ottiene plottando il tasso FNMRT sui valori di FMR(T) al variare della soglia T ?
	- La curva Reciver Operating charatteristic sbagliata ma meno sbagliata rispetto alle altre.
- Un sistema biometrico che non commette nessun errore ha una CuRVA ROC  ( più adatto DET) che passa dagli ASSI ?
	-  ( asse in alto e asse in basso). Vero

---

Storia delle impronte digitali :
Prime apparizioni di impronte :
- Impressione su una lampada di terracotta palestinese 400 A.c
- Impressione su cera cinese 300 A.C
- Primo documento biometrico in india 1858

Diffusione nel mondo dei primi sistemi :
- 1901 UK Criminal Identification
- 1901 USA, primo uso ufficiale delle impronte
- 1905 USA, l'esercito inizia ad usare le impronte per schedare i soldati
- 1930 USA l'FBI installa il national finger print.
- 1858 India, Documenti di riscossione, Controllo criminali

Primi sistemi di classificazione :
- Purkinje 1823 , studio sulle impornte
- Sistema di classificazione Henry Londra 1900 :
	- Afferma che il 4% della popolazione ha delle impronte quasi assenti o consumate a tal punto da non essere leggibili.


Come sono Composte le impronte digitali
Le impronte digitali sono creste e valli della pelle sui palmi e sulle dita di molti animali.
Si tratta di tratti biometrici stabili fin dall'ottavo mese di gestazione ( a meno di malattie o gravi incidenti).
Esiste inoltre una parziale simmetria della classificazione fra le dita della mano sinistra e  destra.

Le varie "valli" che troviamo su un impronta digitale prendono il nome di Ridges :
- Sono senza peli
- Contengono moltissimi pori sudoripari
- Non contengono glandi sebacei
- Molte connessioni nervose
- Non si pigmenta

Il sistema di classificazione attuale, utilizza 3 categorie. Le impronte si dividono in :
- ARCH ( Plain e Tented) :
Plain := I ridge entrano da un lato del sample e fluiscono dall' altro lato del sample, con una specie di onda al centro dell'impronta.
Tented := Come prima ma i ridge al centro dell'impronta tendono a formare una specie di triangolo.  ( un core e un delta)
- LOOP ( left, right)
Essentials of a loop:
- Sufficient recurve;
- Un solo delta
- A ridge count across a looping ridge.

- WHORL ( Plain, twin loop, Accidental, Central Pocket)
The type of pattern in which
-  at least two deltas are present
- with a recurve in front of each
- Accidental
	A volte categorizzata come Whorl, combina due tipi diversi di pattern o nessuno

Ognuna delle 3 categorie si divide a sua volta in due sotto-categorie (tranne Whorl), per un totale di 3 categorie e 8 sotto-categorie.
Le classi inoltre non sono distribuite uniformemente. Ad esempio ARCHES è quella contenente meno impronte, mentre loop è la categoria più diffusa.

I sistemi di classificazione attribuiscono una certa categoria ad un impronta in base a :
- L'individuazione degli eventuali core  ( punti di unione) e delta (punti di biforcazione)
- Lo studio degli orientamenti dei ridge.
![[Pasted image 20231106101829.png]]
Le impronte digitali, possono essere applicate nei seguenti contesti :

| Applicazioni forensi                                           | Governative                                                            | Commerciali                                                                      |
| -------------------------------------------------------------- | ---------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Identificazione di :  Corpi  <br>delle persone  <br>terroristi | Carte d'identità  <br>Controllo degli accessi  <br>Controllo documenti | ATM  <br>Accesso a servizi online  <br>Telefoni cellulari  <br>Controllo accessi |


Sitemi AFIS
AFIS ( Autameted FingerPrint Identification System ) è un sistema hardware e software per :
- L'acquisizione e la classificazione dei cartellini decadattilari
- Ricerche delle impronte sconosciute in una banca di dati unica, consultabile dal centro principale e dai terminali distribuiti.

Le ricerche vengono eseguite su set di 10 impronte, sia su frammenti d'impronta rilevati dagli organi di polizia sulla scena del crimine.
Ovviamente i template contenuti nella base di dati, provengono da sample di ottima qualità.

In molti stati la legge permette che gli AFIS vengano integrati al riconoscimento non solo dattiloscopico dei soggetti, ma anche altre informazioni biometriche quali l'impronta vocale, l'iride ed il DNA.

Punti di forza e debolezza :
- Punti di forza
	- È una tecnologia matura, ampiamente controllata, altamente accurata e funzionante in moti ambienti operativi.
	- L'acquisizione dei sample è mediamente facile ed ergonomica
	- Offre la possibilità di usare più dita, aumentando notevolmente l'accuratezza dei sistemi.
- Debolezze
	- Tutti i dispositivi non riescono ad acquisire le impronte di uan frazione della popolazione
	- L'accuratezza tende a degradare nel tempo
	- Essendo largamente applicata ad applicazioni forensi, alcune persone provano senso di disagio nel fornire il tratto biometrico.

Tre livelli di analisi delle impronte
![[Pasted image 20231106101945.png]]

Una impronta può essere esaminata su tre livelli :
- Globale ( livello 1)
- Locale ( livello 2)
- Ultra fine ( livello 3)

- Livello globale
A livello globale possiamo osservare :
- Il flusso delle linee ( arch, loop, whorl o sottoclassificazioni)
- I punti singolari ( core, delta)
- La forma dell'impronta
- L'orientamento
- La frequenza delle righe dell'immagine.

- Livello locale
A livello locale è possibile identificare fino a circa 150 diverse caratteristiche locali delle creste/ridge  ( minutae).
Le due principali caratteristiche sono le terminazioni e le biforcazioni.

Ad esempio FBI per i sistemi automatici AFIS usa solo terminazioni e biforcazioni.
![[Pasted image 20231106102018.png]]

- Livello Ultra fine
A livello ultra-fine è possibili individuare i seguenti dettagli :
- Intra-creste ( i porti della sudorazione)
- Inter-creste ( incipient ridges)

I dettagli del livello 3 sono considerati altamente distintivi, ma si rilevano solo ad altissima risoluzione, almeno 1000 dpi ed in condizioni ideali. Questo in quanto i porti hanno una dimensione di 60-250 micron

Ma le impronte quanto diverse sono ?

In 100 anni ed in milioni di impronte studiate, non si sono ancora trovare 2 impronte uguali di individui diversi. Le impronte possono avere una struttura simile, ma hanno sempre tantissimi punti di diversità, vige la seguente scala :

![[Pasted image 20231106102054.png]]

Anche i gemelli omozigoti ( stesso DNA) hanno impronte diverso, (esame).
Questo in quanto le impronte sono una manifestazione del fenotipo ( dipendente quindi da fattori casuali ed ambientali) pur partendo dallo stesso genotipo (DNA).
Questo dipende dal fatto che i ridge nell’embrione si formano da punti iniziali con un fenomeno di aggregazione cellulare con forti componenti casuali

Non c’è una regola mondiale accettata per dire se due impronte appartengono allo stesso individuo:
- In Olanda, Belgio, Brasile, Portogallo, Svizzera si richiedono 12 punti caratteristici
- In Sud Africa ne bastano 7
	Un esperto procede nel seguente modo :
	- La concordanza nella configurazione del pattern globale che implica una tipologia comune per le due impronte confrontate
	- La concordanza qualitativa, che implica che le minutae corrispondenti siano identiche
	- Il fattore quantitativo che specifica il numero minimo di dettagli minuti che devono corrispondere tra le due impronte ( almeno 12)
	- La corrispondenza dei dettagli di livello 3 che devono risultare correlati.


Sistema AFIS Italiano
Le impronte vengono acquisite con un rapporto 1:1, ad una risoluzione di 500 dpi, in scala di grigi. Per un identificazione giudiziaria è necessaria la presenza di un riferimento metrico.

Attuali criticità :
- Qualità acquisizione dell'impronta, la quale è determinate per l'accuratezza dei sistemi automatici
- Correttezza fase estrazione delle minuzie e matching
	Abbiamo bisogno di un supervisore che :
	- Verifica la qualità del sample 
	- Scarta le impronte latenti o di scarsa qualità
	- Valutazione in fase di matching

La sentenza 2559 del 14.11.1959 espressa dalla Corte di Cassazione indica in 16 17 punti caratteristici il minimo numero di segni uguali per forma, posizione ed orientamento

Futuri miglioramenti nei sistemi AIFS :
- Aumentare a 1000 i dpi la risoluzione standard
- Estensione a sitemi multimodali ( AFIS -> ABIS)
- Acquisizione delle impronte digitali senza contatto
- Automatizzare e aumentare la precisione della estrazione delle minutae
- Aumentare l'interoperabilità


Tecnologie concorrenti sul mercato :

- Sistema della ditta M2SYS :
Si tratta di un sistema multimodale ABIS ( automatic, biometric identification system)
Si tratta di un architettura che supporta il matching biometrico sia in identificazione ( 1;N) che in verifica ( 1:1), il sistema può cercare un match in oltre 200 milioni di irdi o 100 milioni di impronte al secondo

- Sistema della dita dermalog
Come prima si tratta di un sistema multimodale.
È il sistema di riconoscimento biometrico più veloce al mondo, è in grado di cercare un matching con 129 milioni di impronte al secondo

- Tecnologia SDK
Alte prestazioni e tanta integrabilità
Permette di effettuare dei match on card, supporta sia PC, mobile che sistemi embedded.
Abbiamo un accuratezza del 99.98% ed è in grado di eseguire 1 milione di matching al secondo.

---

Qual è il compito dei sensori :
- I sensori devono cercare di catturare la distribuzione di creste e valli sulla pelle .
- Maggiori dettagli catturiamo, migliore sarà la capacità del sistema di identificare/verificare le identità delle persone.
- Possiamo immaginare le impronte come immagini bidimensionali ma anche come superfici tridimensionali.

Tipologie di sensori e caratteristiche :
Esistono due modalità di acquisizione fondamentali :
- Off - line  :
L'acquisizione off-line è divisa in due fasi fondamentali :
- I polpastrelli vengono prima passati su un tampone inchiostrato e poi vengono rotolati su una scheda di carta
- La scheda di acquisizione viene acquisita con uno scanner ottico o telecamera ad alta risoluzione.

Le impronte digitali latenti, sono di tipo off-line ( Ad esempio le impronte trovare su una scena del crimine). Sono prodotte dalle tracce lasciate dal grasso secreto della pela,  esso lascia sulle superfici una traccia evidenziabile con speciali reagenti chimici

- Live - Scan :
Nella modalità live scan, invece l'immagine digitale dell'impronta è acquisita in tempo reale, tramite il contatto del polpastrello con un apposito sensore

I sensori possono essere :
- Ottici, Basati su :
	- Fenomeno della frustated total internal reflection
	- Su scanner tradizionali
	Sfruttano delle proprietà di rifrazione della luce su un condensatore che cattura le informazioni.
- Stato solido, con pixel sensibili alle variazioni di :
	- Capacità
	- Pressione
	- Temperature

Il contatto fra il ridge e la superficie del sensore cambia la capacità del circuito e del singolo pixel.  I Sensori a stato solido che rilevano la temperatura o la pressione hanno forma simile ma circuiti dedicati diversi per il singolo pixel.


- Altro tipo
	- Ultrasuoni
	- Sensori 3D :

Esistono dei sensori che riescono a rilevare la tridimensionalità della impronta digitale.
Nel futuro potranno giocare un ruolo fondamentale se si dimostra che hanno un accuratezza migliore rispetto a quella dei sensori attuali.

Offrono maggiore resistenza agli attacchi


I vari sensori produco delle immagino con delle caratteristiche molto diverse fra loro, i sensori di tipo termico producono l'immagine più accurata possibile.

Un buon sensore pe l'acquisizione di un impronta digitale deve godere delle seguenti proprietà :
- Risoluzione
- Area di acquisizione
- Numero di pixel e bit per pixel
- Contrato
- Distorsione geometrica

In alcune applicazione, oltre alle caratteristiche citate in precedenza può essere utile tenere in considerazione anche i seguenti parametri :
- Numero di frame per secondo
- Presenza meccanismi HW/SW sul sensore per il rilevamento automatico della presenza del dito e delle condizioni. Il sensore effettua l'acquisizione solo se si verificano le condizioni ideali.
- Supporto per comunicazioni crittate
- Sistemi operativi supportati, driver
- Librerie e presenza di documentazione

Esempi di alcuni sensori commerciali


| None                        | Risoluzione               | Velocità | Caratteristiche      |
| --------------------------- | ------------------------- | -------- | -------------------- |
| Google nexus 6p fingerprint | 508 dpi (160\*160 pixels) | 600 ms   | Dry/wet fingerprints |
|Iphone6 finger sensor|500dp|170 um|Lavora anche con protezione|
|Synptics sensor|||Tecnologia under the glass, rende il sensore meno invasivo|

Esempio di sistema multimodale
![[Pasted image 20231106102658.png]]
TVIP4FF = Si tratta di un sistema multimodale in grado di eseguire Facial recognition, riconoscimento impronta digitale, RFID, pin.

- Ha delle ottime performance e accuratezza
- Live finger detection
- Ha una capacità di 4000 impronte digitali, 2000 facce e 10.000 card credentials


Problemi di acquisizione
Nella fase di acquisizione, si possono verificare una serie di problematiche :
- Pressione del dito
Come cambia un impronta con una maggiore o minore pressione del dito sul sensore :
- I ridge da discontinui tendono a diventare continui
- Iniziano a vedersi :
	- I pori sono sempre presenti
	- Incipients ridge ( presenti nel 45% della popolazione (*)
- Quando la pressione diventa troppa, iniziano ad unirsi i ridge fra loro con gli incipients ridge.
![[Pasted image 20231106102733.png]]

- Roto traslazioni e deformazioni
Le parti in contatto con il sensore tendono a non ruotare/spostarsi con il dito, creando una deformazione non lineare, creando così una roto-traslazione.
![[Pasted image 20231106102749.png]]

Rappresentazioni delle impronte
La rappresentazione delle impronte digitali in un sistema biometrico dipende dal :
- Sensore impiegato :
	- Ottico
	- Stato solido
	- Altro tipo
- Livello di analisi :
	- Globale
	- Locale
	- Ultrafine
- Caratteristiche che si estraggono :
	- Posizione dei ridge ( orientamento. Forma)
	- Minuzie ( coordinate, orientamento, tipo)
	- Pori (coordinate)

Il sample della impronta è una immagine in toni di grigio quandi si controlla :
- Risoluzione
- Bit per pixel

Un esempio : L'FBI digitalizza le impronte del DB nazionale a 100 DPI con 8 bit per pixel. Una cartella con 10 impronte occupa circa 10 MB.

Formati di compressione :
- Usando un formato "lossless", con le impronte si ottiene un fattore di compressione 2:1, troppo poco per un archivio di grandi dimensioni. Il formato di compressione è interno a sistema, viene utilizzato per salvare le immagini sul DB al fine di non utilizzare troppo spazio di memorizzazione.
- Esistono dei formati di compressione appositi per le immagini di impronte digitali :
	- L'FBI e il NIST americano usano il seguente algoritmo (WSQ) Wave scalar Quantization.

Formati di interscambio :
Oltre al formato di rappresentazione interna del templare, nel sistema biometrico ( che può essere privato o segreto essendo del produttore), esistono formati di interscambio dei dati fra istituzioni/aziende

ISOC/IEC 19794 è un documento ISO che regola i "biometric interchange formats"

Unicità delle impronte :
È possibile stimare ( come fece Galton) la possibilità che due persone abbiano le stesse minuzie. SI tratta del classico problema intrapreso da un sitema biometrico oppure da un esperto di impronte digitali.

Formulazione del problema :
Data un impronta con N minutiae, è possibile calcolare la probabilità di condividere q minutiae con un altro template contenete m minutiae.

Probabilità ( M, m, n, q )
- N = nuemro minutiae prima impronta
- Q = minutae condivise tra le impronte da confrontare
- m = minutiae altro template
- M = AREA DI OVERLAP / AREA DI TOLLERANZA = A/C

Il numero di minutiae in comune q domina nella comparazione tra due impronte. In realtà nella pratica abbiamo a disposizione molti parametri in più, come ad esempio le posizioni dei pori, il numero di ridge, la posizione dei core, di conseguenza la stima diventa ancora più conservativa.

---

Nel modulo di estrazione delle feature si eseguono tipicamente i seguenti passi :
- Filtraggio iniziale
- Manipolazione della immagine ( enhancement)
- Estrazione delle feature
- Codifica (*)

In questa lezione ci occuperemo delle prime due fasi
Filtraggio iniziale
Fra i filtraggi iniziali usati di solito in genere troviamo :
- Contrast stretching :
Le immagini delle impronte digitali hanno di solito dei toni di grigio molto limitati. L'operazione di contrst stretching allarga la dinamica dell'immagine.
![[Pasted image 20231106103853.png]]
Andiamo ad allargare l'istogramma dell'immagine. Ogni pixel viene rimappato, ottenendo un maggiore contrasto. Andiamo di conseguenza ad distribuire la distribuzione dei grigi nell'immagine.

- Histogram manipulation :
L'istogramma di una immagine può essere mappato in un altro istogramma mediante diverse funzioni. Ad esempio il logaritmo permette di evidenziare delle variazioni sottili di toni di grigio in una immagine che aveva già una dinamica elevata.

Un istogramma è prendere un pixel alla volta ed aumentare i bin che contiene tutti i pixel con un certo valore, da 0 a 255 se usiamo la codifica a 8 bit.

Filtraggio più ottimizzato rispetto a prima, non andiamo ad aumentare solo il minimo e il massimo.

- Wiener filtering  :
Quando si conoscono le caratteristiche spettrali dell'immagine e del rumore si usa il filtro di wiener.
Permette di andare ad attenuare il rumore ed ad amplificare il segnale che ci serve, agendo su ogni pixel.

- Normalization :
L'obiettivo della normalizzazione è quello di standardizzare le variazioni di grigio dei ridge in tutta l'immagine, per agevolare gli algoritmi successivi.

Andiamo in questo modo a gestire la variabilità tra le immagini  ( con diverso contrasto) che un sensore può catturare, in questo modo gli algoritmi successivi possono lavorare con meno casi possibili.

L'algoritmo prende un pixel alla volta e lo porta ad un valore fissato di media e varianza nell'immagine finale.

Non equivale ad una equalizzazione dell'istogramma, in quanto il filtraggio può essere programmato per lavorare anche localmente.


Una volta che abbiamo un immagine standardizzata, possiamo andare ad eseguire la segmentazione, estraendo dall'immagine solamente i ridge che mi servono :
Un algoritmo di segmentazione divide ciò che non ci interessa ( background) da quello che ci interessa (foregorund) . I ridge vengono identificati in quanto in un intorno locale presentano una varianza di toni di grigio molto alta.

L'immagine viene divisa in blocchi ( ad esempio 16*16), viene calcolata la varianza locale  tra i toni del grigio del blocco e vengono scartati i blocchi sotto ad una soglia prefissata.

Blocco troppo piccolo := troppe poche informazioni, non riesco a calcolare la varianza

Blocco troppo grande := non riesco  a definire bene il contorno dei componenti dell'immagine che mi servono.


Inoltre un impronta/ immagine generica, presenta delle regioni con diversa qualità :
Diversa qualità dovuta a :
- Diversa pressione
- Tagli, abrasioni
- Uso non corretto

DI solito si distinguono le regioni che compongono l'immagine in 3 categorie
- Well-defined
- Recoverable
- Unrecoverable ( un AI non può inventarsi delle caratteristiche non esistenti)


Manipolazione immagine ( enhancement)
Obiettivi :
- Migliorare la chiarezza della struttura dei ridge nelle regioni dove è possibile
- Marcare le regioni dove non è possibile estrarre un informazione perché è presente troppo rumore

In entrata avremo quindi un immagine a toni di grigio, in uscita un immagine a toni di grigio o binarizzata a seconda dell'algo utilizzato.

Come è possibile raggiungere tali obiettivi :
Per ottenere i massimi risultati nell'evidenziare la struttura dei ridge in un immagine occore ricorrere ai filtri adattivi o contestuali

- Filtri contestuali
Questa categoria di filtraggi per le immagini modifica automaticamente i propri parametri per meglio adattarsi al mutare delle condizioni delle immagine, i parametri presi in considerazione sono :
- Distanza fra i ridge media , la quale è fissa
- Orientamento dei ridge, si muovano con una certa linearità
- Livello di rumore presente

Tali filtri si basano sul concetto di convoluzione :
![[Pasted image 20231106104154.png]]

L'operazione \* non è una moltiplicazione ma è un operazione di filtraggio :
- Viene costruito un kernell di dimensione 3\*3 più piccolo dell'immagine di partenza. 
- Verrà preso un blocco di dimensione 3\*3 dall'immagine di partenza, dove ogni pixel dell'immagine verà sovrapposto al kernel. L'immagine di uscita verrà costruito un pixel alla volta.
- Viene moltiplicato pixel \* pixel un singolo pixel dell'immagine con un pixel del kernel. Il pixel dell'immagine di uscita terrò conto di quello che succede nel blocco originale dell'immagine e del contorno del kernel.
- L'elemento centrale del kernell viene piazzato sopra il source pixel. Il source pixel viene rimpiazzato da una somma pesata di se stesso e tutti i pixel vicini.

In uscita avremo un pixel con un valore alto, quando l'immagine assomiglia al filtro. Nell'immagine di uscita verranno risaltati le parti dell'immagine che assomigliano al filtro.

I filtri contestuali lavorano sull'immagine  in ingresso attraverso un operazione chiamata convoluzione con una maschera di filtraggio.
- A seconda del tipo di maschera usata (kernell) il filtro aumenta/diminuisce alcune caratteristiche piuttosto che altre
- Una parte del filtro controlla la porzione dell'immagine in esame e adatta i parametri della maschera.

Alcune tipologie di filtri :
- Filtro di O'Gorman And Nickerson
La forma particolare di questa maschera è fatta per fare "match" con lo spessore dei ridge, la loro distanza di separazione, il valore massimo e del minimo di un introno del punto di esame

Mediante la rotazione della maschera si cerca anche di fare "match" con la direzione preferenziale di ridge. inoltre questo filtro tende ad attenuare il rumore locale.
![[Pasted image 20231106104255.png]]

- Filtro di Gabor
Viene creato il cosi detto banco dei filtri, preparato per varie angolazioni e varie distanze inter-ridge. Viene quindi estesa il filtro precedente, con l'idea di utilizzare più dita.

La maschera che offre migliore "match" viene impiegata nella convoluzione di quella zona dell'immagine. 
- Quando si analizzano regioni “unrecovable” il filtro viene disattivato per non creare falsi ridge (artefatti).
-  In alcune regioni, tuttavia degli artefatti possono essere introdotti ugualmente.
-  Il filtraggio di Gabor può introdurre effetti di blocchettizzazione



Estrazione delle feature di un impronta
Possiamo estrarre feature dal sample appartenenti a 3 livelli :
- Livello 1 : direzioni dei ridge, core, delta, ridge count
- Livello 2 : minutiae
- Livello 3 L pori, cicatrici
	- Tipicamente vengono studiate le posizioni dei pori attraverso :
		- Segmentazione
		- Operatori morfologici

Estrarre caratteristiche di livello 1 :
- Ridge counting
È una misura dei ridge che attraversano una linea immaginaria passante tra due minutiae

![[Pasted image 20231106104346.png]]

La grandezza del ridge counting pur essendo calcolata partendo dalle minutiae ( livello 2 ) è considerato come appartenente al livello 1, in quanto porta informazioni non localizzate attorno ad un punto ma su cosa succede nell'impronta fra alcuni punti anche lontani fra loro.

- Analisi delle frequenze spaziali :
È una misura di quanto sono stretti o larghi i ridge nelle varie regioni dell'impronta.
Ridge frequency = inverso della distanza media tra due picchi consecutivi

Mappa delle frequenze spaziali := Usando l'informazione ricavata dalla frequenze di ridge per ogni blocco dell'immagine è possibile avere la mappa delle frequenze nell'immagine

![[Pasted image 20231106104456.png]]

- Orientamento dei ridge
	- Non è un calcolo banale
	- Di solito si divide l'immagine dell'impronta in blocchi W x W non sovrapposti. Esiste successivamente una formula che calcola la stima ottimizzata dell'orientamento medio nel blocco.
	- Occorre ora controllare che non vi siano salti di fase, dovuti al fatto che il ridge non ha un verso ma solo la direzione ( da 5 a 175) gradi

In alcuni casi è necessario eseguire un filtraggio passa-basso ( una media spaziale), per evitare comunque salti bruschi vicino ai punti singolari come core e delta.

- Il calcolo esatto e robusto dell'orientamento dei ridge è fondamentale nell'enhacement, nell'identificazione delle minute e nella funzione di matching delle impronte digitali.

Usando la media di orientamento di ogni blocco ( teta(i,j)), si ottiene una mappa degli orientamenti.
Successivamente si può utilizzare il vettore gradiente dell'immagine in un blocco Bij, per produrre mappe nelle quali si visualizza il vettore ottenuto dal modulo e dall'orientamento del gradiente.

![[Pasted image 20231106104541.png]]

- Orientation Field Flow Curves
Le OFFC sono curve ( sintetiche) all'interno delle impronte digitali, la cui tangente è parallela al campo di orientamento dell'impronta.

Sono molto usate per studiare la topologia e per classificare le impronte. In quanto permettono di localizzare in modo robusto la presenza di punti singolari come core e delta attraverso il loro andamento.

Le OFFC si proiettano in uno spazio attraverso le mappe isometriche. L'andamento della proiezione, individua il tipo di punto singolare
![[Pasted image 20231106104554.png]]
Usando Core/Delta e/0 OFFC si arriva ad una percentuale di errore del 3% nella classificazione di una impronta.
Notare come :
- abbassando il numero di classi si alzi il numero di campioni necessari da scansionare, il precision rate tutta via sale.
- si abbassi l’errore di classificazione il problema di classificazione è più semplice)

- Core detection
- Metodo delle normali  :
I punti di core possono essere calcolati intersecando le normali

Se seguendo N ridge e calcolando M normali abbiamo un numero sufficientemente alto di intersezioni in un introno di un punto allora abbiamo trovato un core.
![[Pasted image 20231106104641.png]]
- Metodo di poincare
I punti singolari di un impronta possono essere individuati controllando il valore dell'indice di poincare, calcolato in ogni punto i, j dell'immagine lungo una curva di Np punti. In particolare per l'indice :
- indice = ½ ----> Core
- indice = ½ ----> Delta

Teta è il campo di orientamento
X(k) e Y(k) sono le coordinate del k-esimo punto della curva.



- Estrarre caratteristiche di livello 2 :
Panoramica delle tecniche :
![[Pasted image 20231106104720.png]]
- Metodi di binarizzazione :
I metodi di binarizzazione portano una immagine in toni di grigio in un immagine in bianco e nero dove sono evidenziati i ridge.
- I metodi classici di binarizzazione a soglia globale e a soglia locale nel caso delle impronte non funzionano in modo robusto.
- Funziona in modo robusto per le impronte la binarizzazione adattativa

- Thinning :
L'operazione di thinnig corrisponde a ridurre progressivamente le linee di un immagine binarizzata fino allo spessore di 1 pixel ( scheletro dell'immagine)

L'algoritmo deve anche (se possibile) riempire i buchi nei ridge per non creare profili di questo tipi :
![[Pasted image 20231106104751.png]]
- Identificare una minuzia
Esaminando l'intorno di ogni punto lungo un ridge di una immagine scheletrizzata è immediato trovare se siamo su fine riga o una biforcazione.

Basterà contare le intersezioni lungo il perimetro della matrice 3\*3 attorno al punto :
- Una intersezione fine riga
- Due intersezioni -> ridge passante
- Tre intersezioni biforcazione.

Il perimetro della matrice è quello al difuori del bordo del quadrato evidenziato.
![[Pasted image 20231106104914.png]]
Se le intersezioni sono maggiori di 3 occorre esaminare meglio i casi per stabilire se siamo in casi particolari.

- Metodi di post processing
I moduli di post processing, hanno il compito di rimuovere le minutiae spurie introdotte dai moduli precedenti per errore.

L'errore che si può commettere è quello di togliere una minutia corretta commettendo quindi errori.

Esistono due categorie principali di post processing :
- Structural post processing  :
I moduli di structural post processing sono tipicamente basati su regole.
Controllano le caratteristiche dello scheletro adiacente alla minutia candidata.
Le regole maggiormente usate sono 8.
![[Pasted image 20231106104941.png]]

- Minutiae filtering gray scale
I moduli di post processing sono basati su toni di grigio, vengono analizzate le regioni dell'immagine a toni di grigio adiacenti alla minutae da tenere o scartare.

Si possono usare vari algoritmi per effettuare questo controllo ( reti neurali).

---

Occupiamoci ora del problema di matchare due impronte digitali.

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

---

Furti d'identità
I furti d'identità costano centinaia di miliardi di dollari all'anno in USA ( principalmente su carte di credito). L'identificazione mediante impronte sembra essere la soluzione più immediata a questo problema.

In realtà come si sono sviluppate le tecniche anti-spoofing, si sono sviluppate anche negli anni le tecniche spoofing, di conseguenza ad oggi esistono molti modi di attaccare un sistema biometrico :
- Attaccare i canali di comunicazione del sistema ( replay attack), specialmente il canale di comunicazione dal sensore al sistema
- Attaccare moduli specifici ( sostituire alcuni moduli con un cavallo di troia)
- Attaccare il DB con tutti i dati di enrollment
- Ingannare il sensore, di solito presentando un sample ad Hoc finto.

La frode di un sistema biometrico non è un evento impossibile e non necessariamente tecnicamente complesso.

Sensor spoofing :
Tassonomia delle tecniche di attacco ad un sistema biometrico basato sulle impronte fornendo ingressi contraffatti (attacco al sensore), esistono due metodi per frodare il sensore :
- Friction ridge falsi
	- Gomma
	- Silicone
	- Gelatina
- Friction ridge veri
	- Amputazioni
	- Trapianti

Analizziamo ora delle frodi che possono essere apportate ad un sistema biometrico :
- FRODE CLASSICA A
	- Supponiamo di avere un utente X, il quale è autorizzato ad entrare nel sistema, esso esegue un enrollment registrandosi con il tratto biometrico L(x)
	- X cede a Y (utente malevolo) il suo tratto biometrico o ne permette una copia. Il tratto l(x) viene ora copiato in A(X), in possesso da Y
	- L'utente Y è ora in grado di essere autenticato dal sistema, l'utente malevolo Y è riuscito ad entrare nel sistema.
	- Il tratto A(X) può essere ceduto o copiato e ceduto a più utenti malevoli.
-  FRODE CLASSICA B
	- X ottiene A(Y) tratto biometrico di un utente malevolo Y
	- X dato che ha i permessi per effettuare l'enrollment, registra nel sistema il tratto biometrico A(Y) associandolo a se stesso.
	- Ora Y è in grado di essere identificato/autenticato dal sistema
	- Il tratto A(Y) può essere distribuito a più utenti malevoli
- FRODE CON tratto casuale
	- X viene in possesso del tratto biometrico A(Y) , A(Y) è un tratto biometrico casuale.
	- X registra nel sistema tramite uan fase di enrollemet il tratto A(Y), associandolo a se stesso
	- X è in grado ora di essere autenticato/registrato dal sistema
	- Il tratto A(Y) può essere ceduto o copiato ad altri utenti malevoli.
- Tentativi di frode anomali
	- Amputazioni di dita per rubare automobili di lusso dotate di accensione a chiave biometrica ( frode riuscita)
	- Trapianti delle dita dei piedi su quelle della mano per frodare il programma US-VIST americano ( frode fallita)

Attacchi al sensore
È possibile ingannare un sensore di riconoscimento dell'impronta digitale tramite un dito finto ? La risposta è si e in vari modi
- FAKE fingers
È possibile ricreare la superficie dell'impronta con vari materiali, la superficie dell'impronta può essere ricreata a partire da :
- Un impronta "lifted" presa da una scena (ad esempio un bicchiere in un bar)
- Da un immagine rubata da un sistema
- Da un dito reale di una talpa

Vediamo ora i risultati che ottiene la clonatura di un impronta di un dito vero  :
La tecnica  utilizzata maggiormente è quella ideata da Matsumoto, permette di duplicare un impronta su un dito reale . Risulta molto semplice, poco costosa ( semplici materiali, plastica, gelatina) e inoltre da buoni risultati.
![[Pasted image 20231106110405.png]]
Nella pratica cosa succede se diamo impasto un impronta finta a vari tipi di sensore ?
- I sensori ottici, non riescono a distinguere le impronte vere da quelle false  
- I sensori capacitivi non riescono a distinguere le dita realizzare in gelatina da quelle vere, tutta via si proteggono dalle dita in silicone.

Risultati del prof Matzumoto :
- Il professore è andato a testare le impronte finte su 11 sistemi commerciali più diffusi sul mercato.
- Il test prevedeva 4 condizioni

| Enroll           | Verification     |
| ---------------- | ---------------- |
| Dito vero        | Dito di gelatina |
| Dito vero        | Dito di gomma    |
| Dito di gomma    | Dito di gelatina |
| Dito di gelatina | Dito vero        |

- Il test venne ripetuto 100 volte, circa 4 volte su 5 i sitemi biometrici sono stati ingannati dal dito artificiale
- Altri test indicano percentuali di spoofing vicine al 90%

È possibile tramite altre tecniche copiare anche le impronte latenti.

- Attacco del nastro
Questa tecnica di spoofing è molto semplice da realizzare :
- Il signor X entra in un ambiante protetto con un sistema biometrico appoggiando la sua impronta sul sensore.
- Il signor Y (impostore) passa subito dopo e soleva l'impronta fresca con un nastro apposito.
- Il signor y evidenzia l'impronta ( povere per impronte), la fotografa ed inizia il procedimento di duplicazione per le impronte latenti
È importante non lasciare il tratto biometrico sul sensore.


Generazione sintetica di impronte
Sono disponibili in letteratura dei generatori di impronte sintetiche che, partendo da numero casuali, sono in grado di generare immagini di impronte perfettamente verosimili.
Questi generatori casuali permettono di simulare delle condizioni ambientali a piacere, ad esempio :
- Sfondi
- Rumore di acquisizione
- Dimensione e forma dell'impronta

I generatori generano un sample di un impronta partendo al contrario, si parte dai punti singolari, si calcola il loro orientamento e infine si aggiungono i ridge e il rumore.

Di solito tali generatori vengono utilizzati per testare dei sistemi biometrici nuovi, senza dover ricorrere a costose campagne di acquisizione mediante volontari. Tutta via tali prove con impronte sintetiche non potranno mai sostituire i test con impronte vere.


Tecniche antispoofing
Anti-Spoofing hardware o software :
- SW
	- Valutando le caratteristiche del campione (nitidezza del rughe e presenza di pori).
	- Il software ha il vantaggio si essere facilmente implementabile e facilmente aggiornabile.
	- Permette di implementare di modelli di machine -learning o di deep learning atti a fare anti-spoofing.
- HW
	- Richiede funzionalità aggiuntive nello scanner di impronte digitali, come il capacità di rilevare impulsi, temperatura e capacità, nessuno dei quali può essere fatto solo nel software
	- L'hardware ha il vantaggio di avere una migliore accuratezza nel rilevare la vitalità di un impronta
	- Più dispendioso, consuma maggiore potenza, introduce latenza.
	
 - Test di vitalità per sensori ottici
Uno degli approcci più comuni al test di vitalità consiste nell'usare uno o più segnali vitali comuni a tutta la popolazione di riferimento :
- Il flusso sanguigno e la sua pulsazione possono essere rilevati mediante luce riflessa o trasmessa attraverso il dito
- La temperatura e la sua distribuzione può indicare se il dito è vivo, morto o fasullo

Gli scanner ottici di tipo live-scan con le tecnologie FTIR ( frustated total internal reflection) o i sensori allo stato solido utilizzano un meccanismo di acquisizione differenziati per le creste ed i solchi delle impronte digitali :
- Resistono agli attacchi portati con immagini 2D fasulle.

I sensori ad alti risoluzione ( > 700 DPI) rilevano i dettagli del 3 livello ( pori, incipient ridges) difficile da imitare in un dito artificiale ( per adesso)

La pelle del dito cambia colore per effetto della pressione, quando esso viene premuto sul sensore di scansione, questo effetto può essere rilevato.

I test di vitalità iniziano solo oggi a diffondersi, molti sitemi commerciali biometrici basati su sensore ottici possono essere frodati con dita di silicone e gelatina


- Test di vitalità per sensori allo stato solido
	- La differenza di potenziale tra due specifici punti della muscolatura del dito ( miografia) può essere utilizzata per distinguerlo con un dito morto.
	- La misurazione dell'impedenza del dito può essere utile per verificare la vitalità del dito
	- La sudorazione continua di un dito e la sua evoluzione temporale sul sensore è un ottimo test di vitalità

- Altri testi di vitalità ( non ancora disponibili ma in fase di sperimentazione)
	- Analisi della deformazione meccanica del dito durante l'acquisione, che distingue il dito vivo da quello falso fatto con gelatine, siliconi, o gomme
	- Nasi artificiali per la rilevazione di odori e sostanze che non sono presenti sulle dita vive ( solventi, gomma)
- Per ridurre gli attacchi sulle comunicazione, possono essere apportare le seguenti tecniche
	- Synaptics: può essere utilizzato il protocollo TLS ( transport Layer Security), per crittare la comunicazione tra il sensore e l'host ricevente.
	- Match in sensor tecnology: ogni scansione di un impronta viene interamente autenticata sul sensore. Il quale inoltre contiene in modo sicuro l'impronta dell'utente usata nelal fase enrolment.

---

