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