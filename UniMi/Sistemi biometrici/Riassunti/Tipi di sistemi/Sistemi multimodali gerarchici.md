Nei sistemi multimodali gerarchici avvengono `acquisizioni in cascata in base al risultato dell'identificazione precedente`.
- In verification `riducono il tempo di verifica`
- In identificazione permettono attraverso la `tecnica del "pruning" di ridurre le porzioni di DB da analizzare mediane indexing`
- Per ridurre il tempo medio di verifica, occorre acquisire prima i tratti biometrici maggiormente accurati, tuttavia in alcune applicazioni è l'utente che sceglie che tratto mostrare.

`Fusione a livello di features`:
Non è semplice andare ad effettuare una fusione delle features, in quanto `abbiamo un eccessiva eterogeneità fra le features` ( per esempio volto con autofacce e impronta con minuzie).
DI solito la fusione è `possibile quando si vanno ad estrarre degli array numerici da ogni features`.

Esempio :
Supponiamo di avere i tratti della mano e del volto :
- Dalla mano si estraggono 14 lunghezze
- Dal volto 25 coefficienti delle autofacce

- Si normalizzano le features
- Si concatenano i due array
- Si calcola :
	- La distanza euclidea fra i template concatenati
	- La distanza fra le singole features
- Si uniscono i risultati e si passano ad un classificatore o regressore

Esistono due approcci `per aumentare ancora le prestazioni se si tiene conto delle caratteristiche singolari di ogni utente`:
- `Ogni utente avrà una distanza personalizzata dagli impostori`, di conseguenza ad ogni utente saranno assegnate delle `soglie di decisione personalizzate`, per ogni tratto biometrico.
	Dalle distribuzioni dei genuini possiamo calcolare il FRR per ogni utente, se fossero stati impostori controllavamo il FAR.
- Si vanno a `pesare diversamente i vari tratti biometrici, in funzione della qualità del sample` acquisito in fase di enrollment e dell'importanza del tratto. Teniamo dunque conto :
	- Qualità del tratto
	- Errore di quel tratto biometrico 
In altra parole si hanno `due set di parametri nella progettazione di un sistema modale, la soglia dei matching ed i loro pesi`.