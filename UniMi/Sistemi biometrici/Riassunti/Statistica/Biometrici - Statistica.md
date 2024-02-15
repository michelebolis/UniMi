Quanto sbaglia un sistema biometrico?
La domanda che ci andiamo a porre è qual è il tasso di errore di verifica/identificazione
Descrivere il funzionamento di un sistema con un solo tasso di errore è quasi sempre sbagliato.

La `soglia` di un sistema biometrico `influisce su come il sistema biometrico funziona e lavora`.

Si impiegano i termini :
- `Genuino` per indicare un `individuo che accede al sistema e ha titolo per farlo`.
- `Impostore` per chi `prova ad accedere senza averne il titolo` (zero effort) .

Casi
- Caso della `verifica`
	Dobbiamo verificare se l'utente è chi dice di essere, si tratta di un problema di `classificazione binaria`.
	
	Dati in ingresso (query) :
	- un insieme di caratteristiche Xq
	- dichiarazione di identità I.
	
	Occore determinare se (I, Xq) appartengono a w1 o w2, dove :
	- W1 indica che la richiesta è vera ( utente genuino)
	- W2 indica che la richiesta è falsa ( un impostore)
	
	Le caratteristiche Xq vengono controllate con le caratteristiche XI ( il template memorizzato nel sistema associato alla identità I)
	
	Regole di decisione per la verifica:
	Si tratta di una `comparazione con soglia`
	$$ (I, X_q) \in {\begin{cases} w_1 \text{ SE }S(X_q, X_i)>=T \\ w_2 \text{ ALTRIMENTI} \end{cases}}$$
	- S è la funzione che misura la similitudine tra XQ ( ingresso) e XI template
	- `T è la soglia prefissata`
	
	S(Xq, Xi) si chiama `similarity score o match score`
	L'impronta inserita viene confrontata con un solo template nel db (1:1).
- Caso dell'`identificazione`
	Nel caso dell'identificazione dobbiamo controllare se i dati biometrici inseriti dall'utente corrispondono ad un insieme di identità registrate, può essere formalizzato nel seguente modo:
	
	Dati in ingresso : un insieme di caratteristiche Xq (query)
	
	L'obbiettivo è quello di determinare l'identità Ik con k appartenente all'insieme {1,2,3,…,M,M+1} dove I1, I2, Im sono le M identità memorizzate nel sistema e Im+1 rappresenta il caso di reiezione (nessuna delle M identità registrare è simile all'ingresso). `Il caso di reiezione è necessario in quanto altrimenti andrei a selezionare l'identità che assomiglia di più all'ingresso autorizzando cosi un impostore`.
	I dati in ingresso vengono confrontati con più templare (1:N) e non più solo con uno come prima
	
	Regole di decisione della identificazione:   
	Si tratta di M comparazioni con soglia
	$$(X_q) \in {\begin{cases} I_k \text{ SE } k=argmax S(X_q, X_{ik} \text{ and } S(X_q, X_{ik}) >=T) \\
	I_{M+1} \text{ altrimenti}\end{cases}}$$
	- Xik è il templare corrispondente alla identità Ik
	- T è la soglia prefissata
	
	In alcuni casi ci si riferisce ad una misura della distanza fra Xq e Xi. 
	`Una grande distanza fra i vettori di feature porta a un basso match score`.


`N template provenienti dalla stessa persona ed acquisiti in tempi diversi non sono mai uguali` (esame)
Esiste sempre una distanza nello spazio delle feature che separa i template anche della stessa persona, Questo è dovuto a fattori come:
- Rumore di acquisizione
- Diversa posa del soggetto
- Diversa illuminazione o sfondo
- Condizione ambientali

Questo porta al fatto che `la soglia T non può essere arbitrariamente abbassata`, altrimenti nessuno sarà identificato (ad esempio se impostiamo T=0) ( esame).
Se si riscontrasse uan distanza nulla fra Xq e Xi S(Xq e XI) = T, probabilmente saremmo di fronte ad un `replay_attack = copia illecita di un template memorizzato che viene riproposto in ingresso per frodare il sistema`.

Chiamo con :
- `Genuine score`: quando `si confrontano le distanze fra template dello stesso individuo`
- `Impostor score`: quando `si confrontano le distanze fra template di individui diversi`

Possiamo avere inoltre due casi di errori possibili :  (esame)
- Il ladro entra in casa perché il sistema biometrico lo ha scambiato per un utente autorizzato ( False Matching, errore di tipo 2) . Questo caso si verifica quando l'imposto score è maggiore della soglia T impostata
- Noi non entriamo in casa perché il sistema biometrico ritiene che il nostro template non assomigli abbastanza a quello registrato ( False non - Matching, Errore di tipo 1) .Corrisponde al caso in cui il genuine score è minore della soglia T impostata.


[[Statistica - FNM e FM]]
[[Statistica - DET e ROC]]
`CMC - Cumulative Match Characteristics`
Nel contesto della `identificazione` si può valutare il grafico CMC.
Supponiamo di cercare un impronta latente, chiediamo al sistema biometrico di scegliere le 10 impronte più vicine a quella cercata, qual è la probabilità che ci sia dentro al pool quella cercata.

La curva rappresenta la `probabilità di identificare una persona in base al pool di impronte che abbiamo selezionato ordinate in base al match score`.
- N = numero persone del DB
- Per ogni individuo k ordino gli R ( = Rank) individui più simili a k.
- Conto le volte che appare k era negli R trovati per tutti k
![[Pasted image 20231106100640.png|300]]
Caratterizzazione degli utenti the Doddington zoo
- SHEEPS (`pecore`): utenti con features molto distintive e `bassa variabilità intraclasse`. Avranno `bassi FMR e FNMR`.
- GOATS (`capre`): Utenti con `alta variabilità intraclasse`. Tendono ad avere `molti False Reject`.
- LAMBS (`agnelli`): Utenti con features che si sovrappongono estesamente con quelli degli altri, hanno una `bassa distanze interclasse`. Un agnello entra al posto di una percora. Hanno un `False Accept Rate alto`.
- WOLVES (`lupi`): Individui `capaci di manipolare il tratto biometrico` (i tratti compartamentali di solito) per impersonare un utente legittimato. Un lupo entra al posto di una pecora. Aumentano il `False Accept Rate`

[[Sistemi biometrici - Modelli statistici]]
[[Valutazioni di un sistema biometrico]]
[[Comparazione dei sistemi biometrici]]