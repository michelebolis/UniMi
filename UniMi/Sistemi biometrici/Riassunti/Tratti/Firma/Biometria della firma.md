Introduzione
Si tratta di un metodo molto diffuso e semplice.
Tuttavia abbiamo una bassa accuratezza.

A differenza dei sensori per la rivelazione dell'iride tutta via il costo del sensore è estremamente basso. I sensori possono essere dei pad più complicati, per misurare varie velocità nella firma, firma dinamica. Oppure dei più semplici schermi touch firma statica.

Come avviene il riconoscimento ? Esso avviene sugli andamenti nel tempo di una serie di valori , viene misurata la dinamica della firma:
- Delle coordinate x, y
- Della pressione
- Dell'azimut
- Dell'inclinazione


Biometria della firma :
- Ragionevolmente unica non solo dal punto di vista ma anche per una serie di caratteristiche :
	- Velocità di scrittura .
	- Angolo d'inclinazione della penna .
	- Accelerazione del movimento .
	- Numero di volte che la penna viene sollevata dalla carta.
- Maggiore applicazione negli ambienti bancari e finanziari
- Firma online :
	l'utente appone la propria firma con una penna speciale o su una tavoletta elettronica in grado di rilevare i parametri descrittivi della firma, che portano alla creazione d un template le cui dimensioni sono intorno ai 1500 byte. 1.5kb
	- Tracciati dei parametri nel tempo che sono comparati in sede di matching ( distanze relative spazio - temporali dei punti singolari).
	- Punti singolari tracciati
		- Inversione di moto
		- Cupsidi delle curve
		- Intersezione delle linee
- Firma offline: tipicamente apposta su un documento cartaceo poi scansionato
	- Abbiamo solo a disposizione l'immagine della firma come sample iniziale.  La dimensione del template offline può raggiungere 1MB se il template è la firma scansionata, diversamente può ridursi.
	- Tecniche di confronto :
		- Studio degli istogrammi delle proiezioni orizzontali e verticali dei toni di grigio.
		- Dislocazione dei tratti all'interno dell'area di firma secondo il metodo extended shadow code. Permette di codificare la firma in un codice, creato sovrapponendo una serie di matrici di segmenti sulla firma e andando a verificare le intersezioni delle ombre della firma con i segmenti della maschera.

Vantaggi  :
- Hardware poco costoso
- Buona accettabilità da parte degli utenti.
- Difficilmente falsificabile ( nel caso della firma online)

Svantaggi :
- Instabilità temporale del campione ( elevata variabilità intraclasse)
- Dimensioni del template
- Numero limitato di applicazioni adatte
- Si hanno problemi per firme molto brevi o troppo semplici ( elevata similtudine interclasse)

Applicazioni :
Banche e transazioni finanziare, per esempio i requisiti della APACS ( association payment clearing service) richiedono un FMR uguale al 0.001% ed un FNMR pari al 5%.

Ad oggi non si hanno sistemi commerciali che hanno tale requisito. Tutta via i sistemi esistenti vengono utilizzati per facilitare il riconoscimento ad un operatore fisico.

ERR = 3% per firma  con le nuove tecnologie