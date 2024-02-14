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