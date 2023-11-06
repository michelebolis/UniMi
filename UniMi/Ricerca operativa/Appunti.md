Programmazione lineare quando:
- le variabili hanno un dominio continuo
- i vincoli sono equazioni e disequazioni lineari (<=, >=, =)
- la funzione obiettivo è una funzione lineare delle variabili

Forma generale problema PL
1. maximize/minimize $z = cx$ funzione $z$ data dalla combinazione lineare di variabili x
2. subject to (introduzione del sistema di vincoli)
	- $A_1 x >= b_1$ con A1 la matrice dei coefficienti e b1 i termini noti
	- $A_2 x <= b_2$
	- $A_3 x = b_3$
	- $x' >=0$ variabile soggetta a condizione di non negatività
	- $x''$ variabili libere / non ristrette

Forma alle disuguaglianze
I problemi di PL sono riformulati nella formula alle disuguaglianze, per avere un utile interpretazione geometrica
Per passare dalla forma generale alla forma alle disuguaglianze occorre eliminare i vincoli di uguaglianza e le variabili libere.

Si puo sempre passare da un problema in forma generale a forma alle disuguaglianze

Eliminazione vincoli di uguaglianza: sostituzione
Eliminazione variabili libere: sostituisco ogni variabile libera con la differenza tra due variabili non libere che introduco

es
Eliminazione uguaglianze

| Item        | $x_1$     | $x_2$      | $x_3$      | Vincolo |
| ----------- | ------ | ------- | ------- | ------- |
| maximize  z | $3x_1$ | $-2x_2$ | $+5x_3$ |         |
| Subject to  | $2x_1$ | $-x_2$  | $-x_3$  | <=  8   |
|             | $3x_1$ | $+2x_2$ |         | >= -6   |
|             |        | $x_2$   | $-2x_3$ | = 1     |
|             |        | $x_2$ ,        | $x_3$        | >= 0        |

Per sostituzione considerando $x_2 -2x_3 = 1$ come $x_2 = 2x_3 +1$

| Item        | $x_1$     | $x_3$         | Vincolo |
| ----------- | ------ |  ------- | ------- |
| maximize  z | $3x_1$ |  $+x_3$ |  -2       |
| Subject to  | $2x_1$ |  $-3x_3$  | <=  9   |
|             | $3x_1$ |  $+4x_3$       | >= -8   |
|             |         $2x_3$ | >= -1     |
|             |         $x_3$        | >= 0        |

Eliminazione variabili libere
Ponendo $x_1 = x_4 -x_5$

| Item        | $x_3$      | $x_4$  | $x_5$  | Vincolo |
| ----------- | ------- | --- | --- | ------- |
| maximize  z | $+x_3$  | $+3x_4$    | $-3x_5$    | -2      |
| Subject to  | $-3x_3$ | $+2x_4$    | $-2x_5$    | <=  9   |
|             | $+4x_3$ | $+3x_4$    | $-3x_5$    | >= -8   |
|             | $2x_3$  |     |     | >= -1   |
|             | $x_3$ ,   | $x_4$ ,   | $x_5$    | >= 0    |

Vincolo ridondante: $2x_3 >=-1$

| Item        | $x_3$      | $x_4$  | $x_5$  | Vincolo |
| ----------- | ------- | --- | --- | ------- |
| maximize  z | $+x_3$  | $+3x_4$    | $-3x_5$    |    |
| Subject to  | $-3x_3$ | $+2x_4$    | $-2x_5$    | <=  9   |
|             | $+4x_3$ | $+3x_4$    | $-3x_5$    | >= -8   |
|             | $x_3$ ,   | $x_4$ ,   | $x_5$    | >= 0    |


E' semplice identificare i vincoli ridondanti 
Possiamo poi togliere i termini noti o costanti nella funzione obiettivo perche non cambia il ranking delle soluzioni (poi correggeremo il valore ottimo)
Rendiamo poi coerenti tutte le disequazioni: (tranne quello di condizione di non negatività)
- <= SE obiettivo di massimizzazione
- >= SE obiettivo di minimizzazione

Rappresentazione matriciale
Possiamo rappresentare lo stesso modello in maniera piu compatta come
maximize $w = c^T x$
subject to $A_x <= b$
$x >= 0$

es 


| Item        | $x_3$      | $x_4$  | $x_5$  | Vincolo |
| ----------- | ------- | --- | --- | ------- |
| maximize  z | $+x_3$  | $+3x_4$    | $-3x_5$    |    |
| Subject to  | $-3x_3$ | $+2x_4$    | $-2x_5$    | <=  9   |
|             | $-4x_3$ | $-3x_4$    | $+3x_5$    | <= 8   |
|             | $x_3$ ,   | $x_4$ ,   | $x_5$    | >= 0    |


$$c^T = \begin{bmatrix}1 && 3  && -3\end{bmatrix}$$
$$A = \begin{bmatrix}-3 && 2  && -2 \\ -4 && -3 && 3\end{bmatrix}$$
$$x = \begin{bmatrix} x_3 \\ x_4 \\ x_5 \end{bmatrix}$$
$$b = \begin{bmatrix} 9 \\ 8 \end{bmatrix}$$
Interpretazione geometrica della PL
Ogni soluzione x è un assegnamento di valore alle variabili, quindi un punto in uno spazio continuo ad n dimensioni, con n il numero di variabili.

Ogni vincolo di uguaglianza $ax = b$ corrisponde ad un iperpiano
Ogni vincolo di disuguaglianza $ax <= b$ corrisponde ad un semispazio

Il sistema dei vincoli nel modello alle disuguaglianze corrisponde all'intersezione dei corrispondenti semispazi, un poliedro

I semispazi sono convessi quindi l'intersezione di insiemi convessi è un insieme convesso QUINDI i poliedri sono convessi
Un insieme è convesso quando presi due qualunque punti nell'insieme, tutti i punti dei segmenti fanno parte dell'insieme convesso

Regione ammissibile
I "baffetti" dicono da quale parte il vincolo è violato
![[Pasted image 20231105104952.png]]

Poliedri ottenibili
- Poliedro limitato / politopo
- Poliedro illimitato: esiste una direzione per cui se parto da un punto e continuo per quella direzione, non incontro mai una frontiera 
- Poliedro vuoto: i vincoli sono combinati tali da non avere una soluzione ammissibile (e quindi una regione)

|     |     |
| --- | --- |
| ![[Pasted image 20231105105024.png]]    |  ![[Pasted image 20231105105039.png]]   |

Tutte le soluzioni equivalenti giacciono su uno stesso iperpiano
La funzione obiettivo corrisponde ad un fascio di iperpiani paralleli ordinati come i corrispondenti valori dell'obiettivo
La direzione di ottimizzazione definisce l'ordinamento degli iperpiano del fascio

es
minimize z = 2x1 - 3x2
essendo x2 l'asse delle y e considerando che ha segno negativo, la direzione di ottimizzazione e verso l alto in quanto cosi x1 diminuisce e x2, aumentando, fa diminuire z

![[Pasted image 20231105105130.png]]

Considerando
- Convessità del poliedro = regione ammissibile
- Linearità delle curve di livello della funzione obiettivo
ne derivano 3 casi
- SE poliedro vuoto, non ci sono soluzioni ammissibili
- SE poliedro è illimitato nella direzione di ottimizzazione, allora non esiste un valore ottimo finito
- ALTRIMENTI esiste almeno un vertice del poliedro che corrisponde al valore ottimo, proprietà fondamentale della PL


Forma standard
Poniamo tutti i vincoli in forma di uguaglianza introducendo opportune variabili non negativo di scarto (slack) o di surplus

Mettendo in forma standard un problema alle disuguaglianze con $m$ vincoli e $n$ variabili, si ottiene un modello con m vincoli e $n + m$ variabili tutte non negative

Il sistema dei vincoli è un sistema di $m$ equazioni lineari in $n+m$ variabili
SE non ci sono vincoli ridondanti, la matrice dei coefficienti ha rango $m$
Il sistema quindi ha una soluzione univocamente determinabile SE eliminiamo gli n gradi di liberata fissando n variabili

Ad ogni variabile nulla nella forma standard corrisponde un vincolo attivo nella forma alle disuguaglianze
Fissare $n$ variabili a 0 nella forma standard, corrisponde a scegliere un punto in cui n vincoli sono attivi nella forma alle disuguaglianze

es
dato

| Item        | $x_1$      | $x_2$  | $x_3$  | Vincolo |
| ----------- | ------- | --- | --- | ------- |
| maximize  z | $+x_1$  | $+3x_2$    | $-3x_3$    |    |
| Subject to  | $-3x_1$ | $+2x_2$    | $-2x_3$    | <=  9   |
|             | $-4x_1$ | $-3x_2$    | $+3x_3$    | <= 8   |
|             | $x_1$ ,   | $x_2$ ,   | $x_3$    | >= 0    |

La forma standard è

| Item        |  $x_1$      | $x_2$  | $x_3$       | $x_4$   | $x_5$  | Vincolo |
| ----------- | ------- | ------- | ------- | ---- | --- | ------- |
| maximize  z | $+x_1$  | $+3x_2$ | $-3x_3$ |      |     |         |
| Subject to  | $-3x_1$ | $+2x_2$ | $-2x_3$ | $+x_4$     |     | =  9    |
|             | $-4x_1$ | $-3x_2$ | $+3x_3$ |      | $+x_5$     | = 8     |
|             | $x_1$ , | $x_2$ , | $x_3$ ,   | $x_4$ , | $x_5$    |   >= 0       |


Soluzione di base
Una base è un sottoinsieme di $m$ variabili scelte tra le $n+m$ della forma standard 
$$[ B|N ]$$
Il numero di basi è combinatorio, crescendo esponenzialmente con $m$ e $n$
Una volta scelta la base, il sistema si puo riscrivere come 
$$B*x_B + N*x_N = b$$

La soluzione del sistema $m * m$ che si ottiene dopo aver fissato a 0 le n variabili fuori base è una soluzione di base
Per ottenerla bisogna invertire la matrice B formata dalla base

$$x_B = B^{-1} * b - B^{-1} * N*x_N$$
da cui 
- Variabili fuori base $x_N = 0$ 
- Variabili in base $x_B = B^{-1}*b$

Esistono soluzioni di base non ammissibili quando $x_B < 0$
Per verificare ciò basta controllare che le variabili di base siano ancora >=0


Degenerazione
Quando una variabile in base risulta avere valore nullo, si ha degenerazione in quanto piu soluzioni di base coincidono
Piu di $n$ vincoli sono attivi nello stesso punto in uno spazio ad n dimensioni

![[Pasted image 20231105110734.png]]

Teorema fondamentale della PL
Dato un problema lineare in forma standard
$$z = min\{c^T x : A*x = b, x>=0\} $$
con A di rango $m$
- SE esiste una soluzione ammissibile, esiste anche una soluzione ammissibile di base 
(SE un poliedro non è vuoto, deve avere almeno un vertice)
- SE esiste una soluzione ottima, esiste anche una soluzione ottima di base 
(SE il poliedro non è illimitato verso la direzione di ottimizzazione, ci deve essere un vertice del poliedro che ha il valore ottimo)

Perciò un problema lineare nel continuo può essere risolto come problema combinatorio discreto, limitandosi a considerare solo le soluzioni di base.

Metodi risolutivi
La complessita della programmazione lineare è polinomiale (all'aumentare di n e m) tramite l algoritmo dell'ellissoide (Khachiyan 1979)
Il metodo piu utilizzato per risolvere i problemi di PL è l'algoritmo del simplesso (Dantzig 1947)

L'algoritmo del simplesso non da garanzia di terminare in un numero di iterazioni limitato da un polinomio MA è molto veloce 

L'algoritmo garantisce di terminare in un numero finito di passi, garantendo una di queste tre situazioni
- la soluzione corrente è ottima
- NON esiste una soluzione ammissibile
- NON esiste soluzione ottima finita

L'algoritmo del simplesso procede iterativamente da una soluzione di base ad una adiacente


L'algoritmo del simplesso
Forma canonica
- Dalla forma standard del problema di PL
minimize $z = c^T x$
subject to $Ax = b$
$x>=0$

- Scegliendo una base e permutando le colonne di conseguenza si ha
minimize $z = c^{T}_B x_B + c^T_N x_N$
subject to $Bx_B + Nx_N = b$
$x_B, x_N >= 0$

- Moltiplicando a sinistra per $B^{-1}$
minimize $z = c^{T}_B x_B + c^T_N x_N$
subject to $I_{X_B} + (B^{-1} N) x_N = B^{-1} b$
$x_B, x_N >=0$
con $I$ matrice di identità

La soluzione di base $x_B = B^{-1} b - (B^{-1} N) x_N$

- Sostituendo $x_B = B^{-1} b - (B^{-1} N) x_N$ in z
minimize $z = c^T_B B^{-1} b + (c^T_N - c^T_B B^{-1} N) x_N$
subject to $I_{X_B} + (B^{-1} N) x_N = B^{-1} b$
$x_B, x_N >=0$

- Riscrivendo z
minimize $z = z_B + \overline{c}^T_N x_N$
subject to $I_{x_B} + \overline{N}x_N = \overline{b}$

con $z_B$ costante che dipende da B, come abbiamo scelta la base
con $\overline{c}$ perche sono diversi dai c coefficienti iniziali

- Quando si pone $x_N = 0$ si ha $x_B = B^{-1} b = \overline{b}$
SE $\overline{b}$ >= 0 ALLORA la soluzione di base è ammissibile 

Esistono quindi un numero combinatorio di forme canoniche, tante quante le possibili scelte della base
Un problema di PL è in forma canonica SE e SOLO SE
- i coefficienti delle variabili di base, $x_B$, formano una matrice identità $m * m$
- le variabili di base $x_B$ NON compaiono nella funzione obiettivo

La forma canonica è forte SE e SOLO SE i termini noti dei vincoli sono non negativi, $\overline{b} >=0$
Una forma canonica debole implica una soluzione di base non ammissibile 


Una volta posto in forma canonica un problema di PL si puo rappresentare in una matrice, tableau.
E' una struttura dati fondamentale sulla quale opera l'algoritmo del simplesso

es

| Item       | $x_1$   | $x_2$   | $x_3$   | $x_4$   | $x_5$ | Vincolo |
| ---------- | ------- | ------- | ------- | ------- | ----- | ------- |
| minimize z | $-x_1$  | $-2x_2$ |         |         |       |         |
| subject to | $-x_1$  | $+2x_2$ | $+x_3$  |         |       | = 8     |
|            | $x_1$   | $+x_2$  |         | $+x_4$  |       | = 10    |
|            | $x_1$   |         |         |         | $x_5$ | = 7     |
|            | $x_1$ , | $x_2$ , | $x_3$ , | $x_4$ , | $x_5$ | >= 0    |

Forma canonica

| $-z_B$ | $\overline{c}^T_N$    | 0    |
| ------ | --- | --- |
|   $\overline{b}$     | $\overline{N}$    | $I$    |

| 0   | -1  | -2  | 0   | 0   | 0   |
| --- | --- | --- | --- | --- | --- |
| 8   | -1  | 2   | 1   | 0   | 0   |
| 10  | 1   | 1   | 0   | 1   | 0   |
| 7   | 1   | 0   | 0   | 0   | 1   |

Pseudocodice algoritmo del simplesso
```c
while (!Infeasible(b,c)) AND (!FeasibleBase(b)) do
	Pivot(A,b,c)
if Infeasible(b, c) then
	"Stop: problema inammissibile"
else 
	while (!Optimal(c)) AND (!Unbounded(A, c)) do
		Pivot(A, b, c)
	if Optimal(c) then 
		"Stop: soluzione ottima"
	else 
		"Stop: problema illimitato"
```

Nella prima parte si trova una soluzione di base ammissibile.
Wile finche la base non è Ammissibile e non abbiamo dimostrato che il problema è Infeasible
L'iterazione fondamentale del simplesso è il Pivot step

SE il problema è inammissibile, allora l algoritmo termina
Nella seconda parte si cerca una soluzione ottima
Ogni iterazione conserva l ammissibilita
O si trova la soluzione ottima o si scopre che il problema è illimitato

Infeasible = Ammissibile
Unbounded = Test che verifica che il problema sia illimitato

- Pivot(A, b, c)
Ogni iterazione consiste in un cambio di base
Una variabile in base esce dalla base e una variabile fuori base entra in base 
Geometricamente è come se ci muovessimo dal un vertice a un vertice adiacente

1. Si scegli un elemento pivot positivo posto su una colonna fuori base
2. Divido la riga del pivot per il pivot, in modo che il pivot diventi 1
3. Sottraggo ad ogni riga diversa da quella del pivot, la riga del pivot moltiplicata per $a_{ic}$ cioè il coefficiente sulla riga i-esimo e sulla colonna del pivot. Nella colonna del pivot compariranno tutti 0 tranne il pivot. entra quindi in base la colonna del pivot ed esce di base la colonna corrispondente alla riga del pivot

es

| 0   | -1  | -2  | 0   | 0   | 0   |
| --- | --- | --- | --- | --- | --- |
| 8   | -1  | 2   | 1   | 0   | 0   |
| 10  | 1   | 1   | 0   | 1   | 0   |
| 7   | 1   | 0   | 0   | 0   | 1   |

1. Scelgo 2, quindi riga = 1, colonna=2

| 0   | -1  | -2  | 0   | 0   | 0   |
| --- | --- | --- | --- | --- | --- |
| 8   | -1  | ==2==   | 1   | 0   | 0   |
| 10  | 1   | 1   | 0   | 1   | 0   |
| 7   | 1   | 0   | 0   | 0   | 1   |

2. Divido la riga 1 per il pivot, quindi 2

| 0   | -1  | -2  | 0   | 0   | 0   |
| --- | --- | --- | --- | --- | --- |
| 4   | -1/2  | ==1==   | 1/2   | 0   | 0   |
| 10  | 1   | 1   | 0   | 1   | 0   |
| 7   | 1   | 0   | 0   | 0   | 1   |

3. Sottraggo ad ogni riga tranne la 1, la riga 1 moltiplicata per 

| 8   | -2  | 0  | 1   | 0   | 0   |
| --- | --- | --- | --- | --- | --- |
| 4   | -1/2  | ==1==   | 1/2   | 0   | 0   |
| 6  | 3/2   | 1   | -1/2   | 1   | 0   |
| 7   | 1   | 0   | 0   | 0   | 1   |

Entra in base la colonna del pivot, quindi la 2 ed esce dalla base la colonna corrispondente alla riga del pivot, cioe la 1

| Vettore delle x | |  z   |  |
| --------------- | ---| --- | --- |
| prima | dopo | prima | dopo | 
| 0     | 0    | 0 | -8 | 
| 0     | 4    | | |
| 8     | 0    | | |
| 10    | 6    | | |
| 7     | 7    |                |     |




Interpretazione
- Algebrica
Il tableau è un sistema di equazioni
L'iterazione corrisponde a riformare in modo equivalente il sistema di m equazioni e n variabili
Si prende la riga del pivot riscrivendo l'equazione nuova incognita =... e poi per sostituzione otteniamo un nuovo sistema

es
Da $x_3 = 8+x_1-2x_2$  
a $x_2 = 4+\frac{1}{2}x_1 -\frac{1}{2}x_3$

Applico poi la sostituzione di $x_2$ nel sistema

- Geometrica
Associato ad ogni vincolo un indice, la corrispondente variabile che quando è a 0, il vincolo è attivo
indice (1) è associato a $x_2$ e (2) a $x_1$ perche quando $x_1=0$, allora è attivo $x_2$

es
![[Pasted image 20231105152510.png]]

Per determinare l'elemento pivot sono necessarie una regola di scelta della colonna e una regola di scelta della riga


Test di ottimalità: Optimal(c)
I test di otttimalita Optimal(c) riguarda i coefficienti di costo ridotto
z = zB + csegnato^T N * xN
I coefficienti csegnato indicano di quanto aumenterebbe la funzione obiettivo da minimizzare SE le variabili fuori base xN aumentassero di valore, cioè entrassero in base

Quando tutti i coefficienti di costo ridotto sono non negativi, non esistono direzioni ammissibili miglioranti e questo garantisce l'ottimalità della soluzione correte, SE è ammissibile
z* = zB

OSS possono esistere soluzioni degeneri nelle quali la condizione di ottimalità risulta verificata o meno a seconda della scelta della base


Regola di scelta della colonna
Per ogni iterazione dell'algoritmo del simplesso si sceglie una colonna, variabile entrante in base, che abbia costo ridotto negativo. Facendo entrare tale variabile la funzione obiettivo migliora (passi sempre miglioranti)

Ci possono essere diversi modi per effettuare tale scelta, quando ho piu colonne con costo ridotto negativo

es
...

Dobbiamo stare attenti ai casi degeneri che potrebbe causare dei cicli infiniti
La regola di scelta della colonna garantisce che l'algoritmo del simplesso raggiunge l'ottimalità
Diverse strategie
- colonna scelta casualmente tra quelle con costo ridotto negativo
- colonna col minimo coefficiente di costo ridotto
- colonna che produce il maggior miglioramento di z (passi di Pivot piu efficaci)
- la prima colonna con costo ridotto negativo (regola di Bland permette di NON generare mai cicli infiniti) 

Regola di scelta della riga
Scelta la variabile che entra in base, è necessario scegliere la variabile uscente dalla base. Tale scelta deve garantire l'ammissibilità
Data la variabile entrante xj, cioe lo spigolo del poliedro lungo il quale la soluzione cambia, l unica possibilita corretta è
- muoversi verso l'interno del poliedro
	- considerare solo candidati pivot aij positivi
- fermarsi appena si incontra una soluzione di base
	- tra le righe i ad essi corrispondenti, scegliere quella che rende minimo il rapporto tra il termine noto bi e il candidato pivot aij

Nel caso di parità di rapporto minimo, la regola di Bland impone di scegliere la riga di indice minimo (garanzia di assenza di cicli negativi)


Test di illimitatezza
SE non esistono candidati pivot positivi su una colonna con costo ridotto negativo, il problema è illimitato


Variabili limitate
Le variabili puo essere limitate sia inferiormente che superiormente
I vincoli x >= I e x <= U possono essere trattati come vincoli qualsiasi aumentando pero le dimensioni del modello

Estendiamo la definizione di soluzione di base, considerando che una variabile fuori base:
Una soluzione di base estesa SE è una soluzione nella quale n variabili hanno valore pari al loro limite inferiore/superiore e le altre m formano un sistema lineare indipendente cioe una base

L'algoritmo del simplesso puo lavorare con le soluzione di base estese


Inizializzazione
L'algoritmo del simplesso mantiene l'ammissibilità e cerca l'ottimalita quando è inizializzato con una soluzione di base ammissibile MA puo accadere che la soluzione di base iniziale non si ammissibile
Modi
- Metodo delle variabili artificiali
Sato un modello PL in forma standard (anche in forma non canonica) con n variabili e m vincoli
Si introduce una variabile artificiale ui >= 0 con coefficiente unitario in ogni vincolo i=1, ..., m definendo cosi un problema artificiale

Tutte le variabili artificiali u compaiono in e^T con coefficiente 1

Vale la prima condizione per la forma canonica ma non la seconda
I coefficienti di u formano una matrice identita MA le variabili u non hanno coefficienti nulli nell'obiettivo
Per ottenere una forma canonica si effettua la sostituzione nell'obiettivo
ui = bi - somma da j=1 a n aijxj 
Ottengo la riga 0 del tableau in forma canonica

La soluzione iniziale x=0, u=b è ammissibile per costruzione e quindi si puo eseguire l'algoritmo del simplesso sul problema artificiale

SE il valore ottimo del problema artificiale è nullom allora si è trovata una soluzione ammissibile per il problema originario (tutto le u=0 e le x invece hanno dei valori)
ALTRIMENTI si è dimostrata l'inammissibilita del problema originario

Vantaggio: si puo sempre applicare
Svantaggio: puo comportare nella prima fase molti passi di pivot, almeno n passi di pivot e inoltre lavora su un tablue piu grande

- Metodo delle variabili artificiali
partendo da un problema in forma alle disuguaglianze, riscrivo in modo che il termine noto b sia >= 0.
Posso usare le variabili di slack o surplus come variabili artificiali

Per i vincoli di <=: introduco variabili di slack positive
Per i vincoli di >=: introduco variabili di slack negative

Le variabili di slack per i vincoli soddisfano gia la prima condizione per la forma canonica

Sia h l indice del vincolo col massimo valore del termine noto.
Sottraggo ad ogni vincolo >= h
Nel vincolo i-esimo, compare col segno positivo, formando cosi una matrice identita

Bisognera introdurre variabili artificiali per il vincolo h e per i vincoli in I3

- Metodo big M
Anziche eliminare dalla formulazione del problema artificiale le variabili x, è possibile mantenerle e penalizzare nell'obiettivo le variabili u con coefficienti molto grandi

Vantaggio: non serve una fase di inizializzazione
Svantaggio:
- il valore M potrebbe provocare instabilità numerica
- non è detto che sia facile determinare il valore appropriato per M

- Metodo di Blainskki-Gomory
L'algoritmo trascura temporaneamente la funzione obiettivo e minimizza una misura dell'ammissibilita risoetto ad un vincolo violato, ripetendo l operazione per tutti i vincoli violati finche non raggiunge un abse ammissibile oppore dimostra che il proble è inammissibile

Per ogni vincolo violato una misura della violazione è data dal valore assoluto della corrispettiva variabile, valore negativo