Come capire se - la statistica che sto utilizzando è ben focalizzata

Popolazione $X$, di cui $X_1, …, X_n$ campione
Parametro $\Theta$, quantita $\tau(\Theta)$
Una statistica t è NON deviata/ NON distorta / corretta rispetto a $\tau(\Theta)$ SE $E(t(X_1, …, X_n)) = \tau(\Theta)$
Valore atteso infatti coglie la centralità. I valori assunti da $X_1, …, X_n$ devono oscillare attorno al valore sconosciuto $\tau(\Theta)$

MA io non conosco $\tau(\Theta)$

SE esiste uno stimatore non distorto, è unico? NO
Controesempio:
$X_1, …, X_n$ da popolazione $X$, $E(X)= ?$,
1. Uso media campionaria QUINDI $E(X) = E(\overline X)$
2. Ora considero $t(X_1, …, X_n) = X_1$ QUINDI $E(X) = E(X_1) = E(T)$ anche in questo caso è non distorto

QUINDI ci sono due stimatori non distorti

es
$\tau(\Theta)=E(X)$
$t(X_1, …,X_n)=\overline x =\frac{1}{n}*\sum_{i=1}^n X_i$ 
La media campionaria è una statistica non distorta per il valore atteso? SI
`DIM`
$E(t(X_1, …, X_n)) =? E(X)$
$E(\overline X) =? E(X)$
$E(\frac{1}{n}*\sum_{i=1}^{n}X_i)=?E(X)$
$\frac{1}{n} * \sum_{i=1}^{n}E(X_i)=?E(X)$
Fissando un $i$: $\frac{1}{n}* n * E(X) = E(X)$ VERO