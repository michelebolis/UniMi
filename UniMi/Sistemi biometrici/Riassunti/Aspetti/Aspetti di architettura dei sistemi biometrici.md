Struttura di un sistema biometrico :
Viene divisa in due fasi:
- Struttura Generale della parte di `enrollment`:
	- L'impronta viene acquisita attraverso un opportuno sensore
	- Successivamente viene effettuato un controllo di qualità ( per non inserire nel database template di scarsa qualità)
	- Successivamente vengono estratte le feature, decodificate ottenendo così il template
	- Il pin o il nome ci permette di associarlo ad un particolare template che stiamo memorizzando. Permettendoci così di effettuare sia l'autenticazione che l'identificazione
	![[Pasted image 20231106093952.png]]
- Struttura generale della parte di `verification con DB`:
	- Visto che ho a disposizione un nome fornito dall'utente, tramite una apposita query sul db posso andare ad estrarre solamente il template associato a quel nome e confrontarlo con quello acquisito.
	- Eseguo un `operazione di matching`, se il matching è superiore ad una certa soglia, l'utente è abilitato ad entrare nel sistema
	![[Pasted image 20231106094018.png]]
- Struttura per identification con DB:
	Lo schema segue quello precedente. Tuttavia `non posso andare a selezionare un template specifico` dal db, ma dovrò andare a confrontare l'impronta acquisita con N template.
- Struttura enrollment e verification con un documento biometrico:
	`I dati non vengono più salvati su DB ma su il documento biometrico`.
	La verifica avviene con solo un template (quello impresso sul documento), il dove avviene questo matching caratterizza il tipo di sistema.
- Un sistema biometrico `multimodale utilizza più di un tratto biometrico, sia fisiologico che comportamentale, in una qualsiasi fase` ( enrollment, verification, identification)  (esame)
	Parto dallo schema generale di identificazione di un sistema mono-modale e la copio in base a quanti tratti biometrici il mio sistema multimodale utilizza.
- Sistemi biometrici distribuiti
	Il termine `distribuito si riferisce ad un sistema biometrico quando i moduli componenti sono separati e collegati in rete`.

	`I sistemi di autenticazione non ha senso che siano distribuiti`.
	`I sistemi di identificazione ha senso che siano distribuiti`
	- Sistema di identificazione in aeroporto
	- Sistema di controllo delle frontiere

Solitamente è il modulo dei Db dei template che viene dislocato rispetto ai terminali, per due principali ragioni :
- Di sicurezza (fisica e logica), bisogna garantire la protezione dei dati sensibili.
- Per collegare DB distribuiti su una LAN/WAN

Modello di Mainsfield e Wayman
![[Pasted image 20231106094126.png]]
Si tratta di un `modello funzionale`, l'impronta registrata da un sensore può seguire due percorsi :
- Se siamo nella fase di enrollment, essa verrà registrata nel data storage
- Altrimenti verrà eseguito un matching.
	Possiamo osservare come nella decisione di ammettere l'utente nel sistema o meno, non viene utilizzato solo il matching score, ma viene utilizzato anche il quality score (qualità del template acquisito) , il quale ci permette di dare un peso al matching score di un determinato tratto biometrico.


- `Sistemi biometrici on card`
Il termine un card si riferisce al fatto che il `template biometrico risiede su una smart card`.

La `smart card non effettua il matching` ( potenza computazionale bassa), viene effettuato su un pc a cui è collegato il sensore di acquisizione.
Non possiede un sensore di acquisizione ( si una un sistema esterno).

Negli anni, tuttavia si sono sviluppate delle card dotate sia di sensore fino ad arrivare a delle matching on card ( con degli algoritmi semplificati) . Diventa quandi difficile frodare il sistema in quanto è tutti locale.

`Il matching sta diventando possibile farlo on card` (esame) 
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