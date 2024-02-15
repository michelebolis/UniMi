Rappresentazione del volto
Ogni immagine $p * q$ pixel viene rappresentata con un punto nello spazio 

Il problema di tale spazio è che ha un altissima dimensionalità:
Un DB di facce di dimensione $p * q$ crea uno spazio delle facce in $!$
I metodi di tipo "Apparance based" analizzano la distribuzione delle facce nel face space.

Lo spazio delle facce costruito con immagini row ($p*q$) ha una `dimensionalità troppo elevata`, le facce possono risiedere in un sotto spazio limitato. Il modo di stabilire il sottospazio crea il metodo di analisi:

$X_{PCA} = W^tX$

Trovare una `trasformazione lineare W che mappa il vettore delle di immagini X in Rn in un sotto spazio di dimensione limitata` l molto più limitata l <<n. 
Il matching avverrà sulle feature $X_{PCA}$ e non sulle immagini X. 

Problema : Come possiamo ridurre le dimensione dello spazio e allo steso tempo "separare meglio i punti ?
Prima soluzione è utilizzare la tecnica `Principal Component Analysis - PCA` o `analisi lineare` ( nelle domande)

La PCA parte dal riquadro del volto la mando nello spazio trasformato dalla PCA e vado a `togliere alcuni assi meno importanti riducendo la dimensionalità`

`La PCA per prima cosa cerca una rotazione dello spazio` (ancora la dimensionalità non cambia) che permette di separare meglio le classi.
In altra parole la `PCA cerca una rototraslazione che permette di mettere la variabilità dei dati tutta nei primi parametri`.

Notare come varia la distribuzione degli stessi punti sugli assi X = (x1,x2) e Xpca ( Xpca 1, Xpca 2).

La PCA è una `tecnica utilissima in molti contesti biometrici`. In genere serve a ridurre lo spazio dei dati in `ingresso senza bisogno di sapere la label dei dati` ( come invece serve nella classificazione).
Permette, partendo da molti dati anche molto diversi fra di loro, di ottenere un numero minore di nuove variabili molto descrittive.

Vantaggi :
- Decorrela massimamente qualunque insieme di punti nello spazio di uscita Xpca
- `Minimizza l'errore quadratico medio` tra i dati ricostruiti Xpca e i dati originali X.

Svantaggi:
- `Non ci sono algoritmi veloci per la sua implementazione`
- È un algoritmo costoso in termini di risorse computazionali per il calcolo degli autovalori e auto-vettori.
- Non usano l'informazione di classe e lavorano solo sulla distribuzione dei punti nello spazio dell facce, indipendentemente se appartengono alla stessa classe o no. Linear discriminat analysis, tecnica basata sulle autofacce che tiene conto della classe di appartenenza.
- Soffrono della variazione di:
	- Illuminazione
	- Posa della testa
	- Alineamento
	- Espressioni facciali

Formulazione della PCA :
Trovare $X_{PCA} = W^tX$ t.c. $W^tSW = V$
Dove :
- X = matrice facce * feauture
- S = matrice di covarianza dei dati
- W = matrice di auto-vettori
- V = matrice di covarianza trasformata, gli autovalori sono $v = [v1,v2,..vn]$

Le facce contenuto nel face space, possono essere analizzate in uno spazio di dimensionalità ridotta.
Inizialmente la PCA esegue una rototraslazione in uno spazio con lo stesso numero di dimensioni, ma gli autovettori non hanno la stessa importanza.
Più è grande il valore dell'auto vettore, maggiore è la sua importanza nella ricostruzione dei dati nello spazio delle feature della PCA ( Xpca)

Autofacce algoritmo :
![[Pasted image 20231115095343.png|300]]
La PCA ci permettere di `calcolare una soglia di distanza fra i punti (facce) nello spazio delle feature utile per il sistema di riconoscimento`:
- Dmax = la distanza fra gli utenti più diversi nel DB
- Dmin = la distanza fra i due utenti più simili

Formule :
- Distanza massima fra gli utenti del DB :
$$d_{max} = max(|X_{PCAi}-X_{PCAj}|) \text{ con } i,j =1,2,...,M$$
- Distanza minima fra utenti del DB
$$d_{max} = min(|X_{PCAi}-X_{PCAj}|) \text{ con } i,j =1,2,...,M$$
- Calcoliamo la distanza con l'utente più  vicino fra tutti gli altri utenti del DB (XPCA è l'utente in ingresso)
$$d_{max} = min(|X_{PCA}-X_{PCAi}|) \text{ con } i =1,2,...,M$$

Casi
- PCA immagine nuova:
	Supponiamo che nel nostro sistema biometrico venga fatto l'enrolment di una nuova immagine Z nel sistema:
	- Se La distanza dz fra Z e il primo vicino ( C ) è oltre dmax ovvero la distanza mai osservata fra gli utenti nel DB -> non è una zebra.
- PCA caso impostore:
	Supponiamo che al sistema si presenti un certo utente F ( il quale non è autorizzato ad accedere).
	La distanza $d_F$ fra F e il primo vicino ( C ) è :
	- Al di sotto di dmax -> Ok, infatti è una zebra
	- Ma oltre dimin -> è un impostore.
- PCA caso genuino :
	Supponiamo che al sistema si presenti un utente D2, il quale è già registrato nel sistema come D e di conseguenza è autorizzato all'accesso.
	
	La distanza dD2 fra D2 e il primo vicino ( D)  è sotto il Dmax ( è una zebra) ed è minore di dmin ( è un genuino con identità D)
	
	È possibile inoltre lavorare nello spazio delle facce :
	- Ricostruire una faccia utilizzando le autofaccie :
	- Calcolare la distanza dalla faccia ricostruita da quella iniziale :
		L'errore indica quanto l'immagine iniziale era vicina alla immagini con le quali abbiamo calcolato le autofacce.
		Se ricostruisco bene l’immagine nuova (errore basso) allora probabilmente era una faccia somigliante a una di quelle memorizzate, se invece l’errore di ricostruzione è alto allora significa che il volto è troppo diverso rispetto a tutti i volti usati per creare il DB delle autofacce ( genuini)