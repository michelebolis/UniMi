Programmazione lineare quando:
- le variabili hanno un dominio continuo
- i vincoli sono equazioni e disequazioni lineari (<=, >=, =)
- la funzione obiettivo è una funzione lineare delle variabili

Forma generale problema PL
1. maximize/minimize $z = cx$ funzione $z$ data dalla combinazione lineare di variabili x
2. subject to (introduzione del sistema di vincoli)
	- A1x >= b1 con A1 la matrice dei coefficienti e b1 i termini noti
	- A2x <= b2
	- A3x = b3
	- x' >=0 variabile soggetta a condizione di non negatività
	- x'' variabili libere / non ristrette

I problemi di PL sono riformulati nella formula alle disuguaglianze, per avere un utile interpretazione geometrica
Per passare dalla forma generale alla forma alle disuguaglianze occorre eliminare i vincoli di uguaglianza e le variabili libere.

Si puo sempre passare da un problema in forma generale a forma alle disuguaglianze

es
...

E' semplice identificare i vincoli ridondanti 
Per eliminare le variabili libere, sostituisco ogni variabile libera con la differenza tra due variabili non libere che introduco
Possiamo poi togliere i termini noti o costanti nella funzione obiettivo perche non cambia il ranking delle soluzioni (poi correggerremo il valore ottimo)
Rendiamo poi coerenti tutte le disequazioni: (tranne quello di condizione di non negativita)
- <= SE obiettivo di massimizzazione
- >= SE obiettivo di minimizzazione

Possiamo rappresentare lo stesso modello in maniera piu compatta come
w = c^T x
Ax <= b
x >= 0

...

Interpretazione geometrica della PL
Ogni soluzione x è un assegnamento di valore alle variabili, quindi un punto in uno spazio continuo ad n dimensioni, con n il numero di variabili.

Ogni vincolo di uguaglianza ax=b corrisponde ad un iperpiano
Ogni vincolo di disuguaglianza ax <= b corrisponde ad un semispazio

Il sistema dei vincoli nel modello alle disuguaglianze corrisponde all'intersezione dei corrispondenti semispazi, un poliedro

I semispazi sono convessi quindi l'intersezione di insiemi convessi è un insieme convesso QUINDI i poliedri sono convessi
Un insieme è convesso quando presi due qualunque punti nell insieme, tutti i punti dei segmenti fanno parte dell insieme convesso

Regione ammissibile
I "baffetti" dicono da quale parte il vincolo è violato

Poliedri ottenibili
- Poliedro limitato / politopo
- Poliedro illimitato: esiste una direzione per cui se parto da un punto e continuo per quella direzione, non incontro mai una frontiera 
- Poliedro vuoto: i vincoli sono combinati tali da non avere una soluzione ammissibile (e quindi una regione)

Tutte le soluzioni equivalenti giacciono su uno stesso iperpiano
La funzione obiettivo corrisponde ad un fascio di iperpiani paralleli ordinati come i corrispondenti valori dell'obiettivo
La direzione di ottimizzazione definisce l'ordinamento degli iperpiano del fascio

es
minimize z = 2x1 - 3x2
essendo x2 l'asse dell y e considerando che ha segnmo negativo, la direzione di ottimizzazione e verso l alto in quanto cosi x1 diminuisce e x2, aumentando, fa diminuire z

Considerando
- Convessita del poliedro = regione ammissibile
- Linearita delle curve di livello della funzione obiettivo
ne derivano 3 casi
- SE poliedro vuoto, non ci sono soluzioni ammissibili
- SE poliedro è illimitato nella direzione di ottimizzazione, allora non esiste un valore ottimo finito
- ALTRIMENTI esiste almeno un vertice del poliedro che corrisponde al valore ottimo, proprietà fondamentale della PL


Forma standard
Poniamo tutti i vincoli in forma di uguaglianza introducendo opportune variabili non negativo di scarto (slack) o di surplus

Mettendo in forma standard un problema alle disuguaglianze con m vincoli e n variabili, si ottiene un modell ocon m vincoli e n+m variabili tutte non negative

Il sistema dei vincoli è un sistema di m equazioni lineari in n+m variabili
SE non ci sono vincoli ridondanti, la matrice dei coefficienti ha rango m
Il sistema quindi ha una soluzione univocamente determinabile SE eliminiamo gli n gradi di liberata fissando n variabili

Ad ogni variabile nulla nella forma standard corrisponde un vincolo attivo nella forma alle disuguaglianze
Fissare n variabili a 0 nella forma standard, corrisponde a scegliere un punto in cui n vincoli sono attivi nella forma alle disuguaglianze

Soluzione di base
Una base è un sottoinsieme di m vairabili scelte tra le n+m della forma standard 
\[B|N]
Il numero di basi è combinatorio, crescendo esponenzialmente con m e n
Una volta scelta la base, il sistema si puo riscrivere come 
B\*xB + N\*xN = b

La soluzione del sistema m x m che si ottiene dopo aver fissato a 0 le n variabili fuori base è una soluzione di base
Per ottenerla biosgna invertire la matrice B formata dalla base

xB = B^(-1) b - B^(-1)NxN
da cui 
xN = 0 e xB = B^(-1)\*b

esistono soluzioni di base non ammissibili quando xB !>= 0
Per verificare cio basta controllare che le variabili di base siano ancora >=0


Degenerazione
Quando una variabile in base risulta avere valore nullo, si ha degenerazione in quanto piu soluzioni di base coincidono
Piu di n vincoli sono attivi nello stesso punto in uno spazio ad n dimensioni

-15min