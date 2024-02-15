Qual è il modello statistico migliore per caratterizzare un sistema biometrico:
- `Sistema di lancio`: `modello aleatorio`. Probabilità che esca il numero 6 (Out=6) = 0.16
- `Sistema di lancio truccato`: non più aleatorio ma `deterministico`, la probabilità che esca 6 è più alta. P(out = 6) = 0.67
- `Sistema classificazione generale` = P(sbagliata classificazione genere)  =0.2.
	Controllo se il classificatore assegna una label sbagliata ad un immagine in ingresso.
	La struttura statistica è la stessa nei casi precedenti. 

Tutti questi modelli rientrano in una categoria più grande la quale prende il nome di `esperimenti/prove di Bernoulli`:
- Ad ogni singola prova si hanno due esiti possibili (binari), 1 successo, 0 insuccesso
- La probabilità P dell'evento successo è costante, la probabilità di successo non cambia nel temo.
- I risultati delle prove sono indipendenti. Non riuso lo stesso sample nelle varie prove.

Il sistema biometrico in autenticazione mostra un tasso di errore stimabile e fissato P.
`P = false true match + true false match`.

L'evento che il SB sbagli un autenticazione è un esperimento/prova di Bernoulli.
Un SB che viene usato in identificazione (1:N) si può modellizzare come N prove di Bernoulli, ovvero un processo di Bernoulli : ( per determinare in generale l'errore del SB)

Variabile Aleatoria X può valere:
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

Che differenza c'è tra la roulette russa e un sistema biometrico ? Nella roulete russa più aumento il numero di tentativi più ho probabilità di sbagliare, stessa cosa in un sistema biometrico, la probabilità di errore viene moltiplicata per il numero di tentativi.
Roulete russa = sistemi biometrici .

Regole per `definire correttamente il tasso di errore P`:  (esame)
- `Regola dei 3`
	Qual è il `tasso di errore più basso p che può essere stimato` con un esperimento di comparazione di N campioni indipendenti.
	
	Se abbiamo un sistema che commette zero errori su N prove, non dobbiamo pensare di avere un sistema con p = 0, ma con il 95 % di confidenza, ovvero `p circa 3/N`.
	Il 95 % delle volte che faremo l'esperimento l'errore sta nell'intervallo tra 0 e 3/n. 
	Altrimenti le nozioni statistiche prima non potrebbero essere vere.
	
	Esempio ;
	Se faccio 300 prove con campioni indipendenti e ho zero errori, allora posso dire che con una confidenza del 95% il mio sistema ha un tasso di errore stimato del p = 3/N ->  3/300 = 0,01 * 100 = 1,0 %
- Estensione della regola dei 3
	![[Pasted image 20231106101456.png|300]]
	Se ho 1000 persone e `ho sbagliato 5 volte`, non vado a dire che con il 95 % della confidenza p è circa 5/n ma che `p è compreso tra 5/n e 10/n`.
- `Da verification a identification`
	Quanto aumentano gli errori `nel mio sistema se uso un sistema di verifica (FNMR, FMR) in modalità identificazione` (FMR n , FNMR n) (esame)
	- $FNMR n = FNMR$  (`i tassi di errori per i genuini non cambiano`)
	Lavorare in autenticazione o identificazione per un utente genuino (registrato nel sistema) non cambia.
	- $FMR n = 1 - (1-FMR)^ N$  (con N numero campioni confrontati)
	Ovvero = 1 - ( la probabilità che non ci sia un False match su tutti i campioni confrontati con N)
	
	N.b  con `FMR piccolo`, l'espressione diventa $FMR n = N * FMR$
	Ovvero l'`errore dei false match aumenta linearmente con le dimensioni dei DB`. L'aumento di errore sugli impostori aumenta linearmente in base al numero di campioni registrati nel DB.
	
	L'errore degli impostori FMR viene gonfiato di molto in identificazione
- `La regola dei 30` (esame)
	Quante persone mi servono per dire con una certa confidenza che l'errore è sterro. La regola dei 30 è `usata per determinare la larghezza del campione biometrico`:
	`Per essere sicuro con un intervallo di confidenza del 90 % che il tasso di errore vero sia tra il +- 30% del tasso di errore osservato ci devono essere almeno 30 errori`.
	
	Ad esempio :
	Se abbiamo 30 errori in 3000 comparazioni di genuini indipendenti, possiamo dire ( con intervallo di confidenza del 90%) che l'errore vero sta tra 0.7% e 1.3%
	
	30/3000 = 0,01 * 100 = 1,0
	Il tasso di errore vero sta sul 30% di 1% (1/30)  ovvero +0.3 - 0.7.

Simulazione :
- Qual è la formulazione esatta del problema della rappresentazione nei sistemi biometrici  ?
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