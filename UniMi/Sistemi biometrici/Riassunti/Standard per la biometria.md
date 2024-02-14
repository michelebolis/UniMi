Standard per la biometria
Standard ISO / IEC 19794 = si occupa dell'interscambio di dati biometrici ( di qualsiasi tipo) fra istituzioni e aziende.

Ma chi sono gli Standard (body) :
Sono organizzazioni internazionali che si occupano della standardizzazione di tutti i protocolli in uso.

In biometria sono importanti i seguenti standard body :
- ISO, IEC
- Alcune organizzazioni informali come Biometric Consortium e BIOAPI. Si tratta di insiemi di aziende che commercializzano sistemi biometrici.

Standard BIOAPI :
Lo standard bioapi già dal 2000 contiene tutte le specifiche di interazioni tra i moduli che compongono un sistema biometrico.

Fornisce un modello di autenticazione ad alto livello per ogni tecnologia biometrica presente sul mercato.

Include le specifiche delle funzionalità di :
- Verifica
- Identificazione
- Enrollement
- Interfaccia di interazione con il DB, in modo tale da permettere al biometric service provider di gestire i template nel db in modo ottimale

BSP = è un termine generale che indica il modulo che gestisce le funzionalità biometriche verso i moduli HW e i layer software necessari alle unità.

Bioapi inoltre fornisce le primitive di gestione dei sistemi biometrici distribuiti :

Permette alle applicazioni di gestire le acquisizioni dei campioni. Gestire l'acquisizione su un modulo client e l'enrollment, identification e verification su un modulo server.


Progettazione di un sitema monomodale :
Il problema della progettazione è molto complesso :
- Vi sono molti parametri in gioco
- Alcuni di essi sono difficilmente stimabili

I parametri da tenera a mente nella progettazione di un sistema biometrico sono i seguenti :
- Interoperabilità
- Gradimento degli utenti
- Accuratezza
- Costi
- Velocità
- Scalabilità
- Usabilità

8 domande da porsi per scegliere il tratto biometrico corretto per il nostro sistema :
- È un applicazione di autenticazione o identificazione ?
	Se l'applicazione è di identificazione, bisogna considerare i seguenti parametri :
	- Scalabilità del tratto
	- Unicità del tratto
- È un applicazione completamente automatica o semi-automatica ?
	Se è semi-automatica bisogna :
	- Prevedere un operatore da affiancare al sensore di acquisizione.
	- Se l'applicazione è remota o situata in ambienti ostili non sempre è possibile avere la presenza costante di un operatore al controllo della acquisizione.
- Gli utenti sono collaborativi / allenati all'utilizzo dei sistemi biometrici ?
	- Esistono degli studi scientifici che dimostrano che se un utente viene istruito all'interazione con i sistemi biometrici, migliorano l'accuratezza e il nuemro di retry necessari nella fase di acquisizione.
	- Particolarmente vero per alcuni tratti biometrici ( impronte, volto) indifferente per altri ( retina)
- Il sitema biometrico deve acquisire gli utenti in modo cover o overt (coperto scoperto ) ?
	- Motivi legati alla privacy
	- Per le caratteristiche del tratto biometrico ( impronte, iride solo overt)
- Gli utenti del sistema sono collaborativi o no ?
	Se i soggetti non sono collaborativi, allora :
	- Scegliere un tratto con una lunga durabilità temporale e che non possono essere cambiati o frodati
	- Evitare tratti biometrici comportamentali ( la voce può essere facilmente alterata rispetto all'iride)
- Quali sono i requisiti sulla capacità di memorizzazione del sistema ?
I tratti biometrici presentano dei template con degli spazi di memorizzazione eteregogenei fra di loro, possono variare da pochi byte per le impronte a molti kbyte per la voce.
- Quanto sono stringenti le richieste sulle performance ( accuratezza, velocità) ?
	- In un sitema multimodale ad esempio se la richiesta di accuratezza non è soddisfatta si potrebbero unire due tratti biometrici veloci .
- Quali tipi di tratti biometrici sono maggiormente accettati dalla popolazione degli utenti ?
	- Il tasso di accettazione di un tratto varia molto dalla etnia e dalla cultura delle popolazione di riferimento.
Ad esempio non si può usare il volto se il 50% della popolazione non lo vuole mostrare.

Classificazione dei sitemi biometrici
- Applicazioni protette dalla privacy
Le applicazioni biometriche proteggono delle informazioni personali che potrebbero in altri casi essere compromesse.
- Applicazioni simpatizzanti della privacy
Costruite tenendo conto di particolari template riguardanti la privacy
- Applicazioni privacy neutre
- Applicazioni invasive per la privacy

Ad esempio alcuni id nazionali.

Vediamo ora se il sitema è favorevole o meno alla privacy in base alle sue caratteristiche.

| Privacy ++ | Privacy -- |
| ---- | ---- |
| Overt ( acquisizione con utente informato) | Cover ( acquisizione all'insaputa dell'utente) |
| Optional ( acquisizione opzionale) | Mandatory ( acquisizione obbligatoria) |
| Autentication | identification |
| Private sector | Pubblic sector |
| L'utente interagisce con il sistema come cliente privato | L'utente interagisce con il sistema come cittadino impiegato. |
| I dati sono salvati in personal storage | Database storage |
| Tipo di tratto comportamentale | Tratto fisico |
| Tratto salvato in template | Tratto salvato in sample |

Confronti tra tratti biometrici :

| . | Finger | Face | Voice | Iris | Hand | Signature |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| maturità | Molto alta | alta | media | alta | alta | Media |
| Tipo di sensore | contatto | Non intrusivo | Non inrusivo | Non intrusivo | contatto | Contatto |
| Sensor cost | <200 | <50 | <5 | <300 | <500 | <300 |
| Template size | <500 | <1000 | <2000 | 256 | <100 | 200 |
| scalabilità | alta | media | bassa | alta | bassa | akta |

Accuratezza -> IRIS > FINGER > FACE > VOICE

Poco Costoso -> VOICE > FINGER /FACE > IRIS


Livelli di accuratezza da impostare
Quali sono i livelli di FMR e FNMR da richiedere ad un sistema sulal singola comparazione nelle varie condizioni ? Ecco alcuni ordini di grandezza considerati necessari

| Modalità | FNMR | FMR |
| ---- | ---- | ---- |
| Autenticazione | 0.1% | 0.1% |
| Identificazione su larga scala 1M di iD | 10% | 0.0001 % meno di 1 errore su 1Milione |
| Screening 500 ID | 1% | 0.001% |

Nella stesura del progetto occore tenere a mente che in caso di fallimento del sistema deve essere previsto un meccanismo di bacup. Inoltre devono essere stimati i costi dovuti ad una violazione o ad un errore nel sistema :
- Stima dei danni se un impostore entra ne sistema
- Sitema dei cosi per il fermo del sistema
- Il costo medio di failure to enroll
- Costo medio per la user education

Passi da seguire per la progettazione di un sistema biometrico :
in input al problema abbiamo le specifiche del problema ( richieste dal committente), le quali sono :
- La velocità
- L'accuratezza ( di solito vi è grande incertezza nella definizione di questa specifica)
- I requisiti di costo/performance

I successivi passi progettuali sono i seguenti :
- Stabilire un protocollo per l'acquisizione dei tratti biometrici
- Scegliere uan rappresentazione interna dei sample adeguata per gli algoritmi di estrazione delle feature scelti.
- Quale tipo di feature estrarre, locali, globali, ecc..
- Con quale algoritmi estrarli
	- Accuratezza
	- Robustezza al failure to enroll, variabilità negli ingressi
	- Occupazione delle risorse di computazione e memoria
- Dati due template quale funzione di matching usiamo per esprimere il concetto di vicinanza fra campioni. Quale algoritmo di matching utilizziamo per implementare la funzione di matching :
	- Resistenza alla variabilità degli ingressi ( failure to match)
	- Occupazione di risorse
- Come organizziamo il DB, quante partizioni ?
	- Numero di template per individuo
	- Organizzare il DB in binning per aumentare l'efficienza nelle operazioni di ricerca


BSP
Biometric servcie plattoform,  si tratta di sistemi biometrici che fanno uso di un architettura web.

Nuove soluzioni per far riconoscimento biometrico basate su cloud.
Vanno a semplificare installazione, uso, gestione e manutenzione del sistema biometrico.

Abbassano i costi ed i tempo per iniziare ad usare un sistema biometrico, specialmente per grandi organizzazioni.
Necessitano di connessioni affidabili o il servizio viene interrotto.