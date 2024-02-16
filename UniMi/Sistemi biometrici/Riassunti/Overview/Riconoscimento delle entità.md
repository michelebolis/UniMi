Il riconoscimento della entità consiste nelle operazione che associa una identità ad un individuo.

Il riconoscimento può essere suddiviso in due categorie :
- Verifica dell'identità (`autenticazione`): "equivale alla domanda: sono chi dico di essere?"
	- `Conferma o nega l'identità dichiarata dall'utente`
	- Metodi one to one (1:1) [[Metodi classici di autenticazione]]
- Ricerca dell'identità (`identificazione`): "chi sono io?"
	- Al sistema biometrico non viene presentato nulla, e `a carico del sistema riconoscere l'identità dell'utente che si presenta`, verificando che sia presente nella lista degli utenti ammessi.
	- Metodi one to many (1:N)
	- Il problema di identificazione può essere :
		- `Chiuso`: ho un insieme di utenti del sistema prestabilito
		- `Aperto`: es videosorveglianze: molto più difficile, l'insieme N si allarga.

Queste due categorie hanno diverse funzioni e complessità di realizzazione diverse.
Di conseguenza tali categorie, autenticazione e identificazione non sono equivalenti
- Abbiamo una autenticazione/`identificazione positiva`: quando si cerca di stabilire con elevata accuratezza che l'utente sia chi dice di essere.
- Abbiamo una autenticazione/`identificazione negativa`: quando si cerca di stabilire con elevata accuratezza se l'utente non è chi dice di essere

Alcuni esempi :
Identificazione Positiva = Un sistema di accesso ad un sito militare controlla la mia iride per controllare se appartengo ad una lista di utenti abilitati all'ingresso.
Identificazione negativa = Un sistema di visione controllata con delle  telecamere se chi passa davanti agli obbiettivi non sia un terrorista presente in una lista.
