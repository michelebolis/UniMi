Dato un modello PL in `forma standard` (anche in forma non canonica) con $n$ variabili e $m$ vincoli
$$1)z = min\{c^Tx:Ax = b, x \in R^n_+\}$$
Con $b\geq 0$ si introduce una variabile artificiale $u_i \geq 0$ con coefficiente unitario in ogni vincolo $i=1, ..., m$ definendo cosi un problema artificiale
$$2) z^a = min\{e^Tu:Ax+Iu=b, x,u \in R^n_+\}$$
Tutte le variabili artificiali $u$ compaiono in $e^T$ con coefficiente $1$

`Vale la prima condizione` per la forma canonica ma non la seconda
I coefficienti di $u$ formano una matrice identità MA le variabili $u$ `non hanno coefficienti nulli nell'obiettivo`
Per ottenere una forma canonica si effettua la sostituzione nell'obiettivo
$u_i = b_i - \sum_{j=1}^{n} a_{ij}x_j$
Ottengo la riga 0 del tableau in forma canonica

La soluzione iniziale $x=0$, $u=b$ è ammissibile per costruzione e quindi si puo eseguire l'algoritmo del simplesso sul problema artificiale (2)

SE il `valore ottimo del problema artificiale è nullo` ($z^a=0$), allora si è trovata una `soluzione ammissibile` per il problema originario (tutto le $u=0$ e le x invece hanno dei valori)
ALTRIMENTI si è dimostrata l'`inammissibilità del problema originario` (1)

Vantaggio: `si puo sempre applicare`
Svantaggio: puo comportare nella prima fase `molti passi di pivot`, almeno $n$ passi di pivot e inoltre lavora su un tableau piu grande

[[Metodo delle variabili artificiali - Ottimizzazione]]