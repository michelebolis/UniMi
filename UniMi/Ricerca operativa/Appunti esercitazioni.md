Gusek
file .dat contiene i dati
file .mod contiene il modello
quando utilizziamo due file separati, dobbiamo andare su Tools -> Use External .dat
ATT .dat e .mod devono avere lo stesso nome

`param` per introdurre un dato
es `param nR := 5`
OSS Inserire sempre i commenti per dire cosa sono 
set R := 1..n introduce un insieme
param v{R} per dire che al vettore v associamo l insieme R

Per dichiarare la matrice param a{A, B} nella sezione dati, prima devo dichiarare le colonne e poi := come nel vettore

I vincoli sulle variabili, vengono messi come elenco quando la dichiaro
var x{P} >=0, >= 5;

Premendo su go ci dice solo che ha trovato una soluzione ottima
Quindi checkiamo in tools generate output file on go

Nel file .out troveremo 
- elenco dei risultati
- tabella dei vincoli (con B in base e con NU fuori base (primo membro = upper bound))
- tabella delle variabili originali (con B in base e con NL fuori base (= lower bound))

