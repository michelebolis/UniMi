OSS $Var(X + X) = Var(2X) = 4 * Var(X) \neq 2 * Var(X)$
$Cov(X,Y)=E((X-\mu_X)*(Y-\mu_Y))$
$$Cov(X,Y)=E(XY)-E(X)*E(Y)$$

DIM
$Cov(X, Y) = E(X*Y-\mu_Y*X-\mu_X*X*Y+\mu_X*\mu_Y )$
$= E(XY)-\mu_Y*E(X)+\mu_X*E(Y)+\mu_X*\mu_Y$
$= E(XY)-\mu_Y*\mu_X+\mu_X*\mu_Y+\mu_X*\mu_Y$
$= E(XY) - E(X) * E(Y)$

Considerando  $\mu_X= E(X)$ e $\mu_Y= E(Y)$
Proprietà:
- Simmetrica: $Cov(X,Y)=Cov(Y,X)$
- Trasformazioni lineari
Data la simmetria se applico una trasformazione su un argomento è uguale che farlo sull'altro
$$Cov(a*X+b,Y)=a*Cov(X,Y)$$
DIM
$Cov(a * X, Y) = E((aX - E(aX)) * (Y - E(Y))$
$= E((aX - aE(X) ) * (Y - E(Y))$
$= aE(X - E(X) * (Y - E(Y))$
$= a*Cov(X, Y)$

$Cov(X + b, Y) = E((X + b)*Y - E(X + b)*E(Y) )$
$= E(XY + bY - E(X)*E(Y) - b*E(Y) )$
$= E(XY - E(X) * E(Y) + b*E(Y-E(Y))$
$= Cov(X, Y)$

$Cov(X+Y, Z) = E((X + Y) * Z) - E(X + Y) * E(Z)$
$= E(X * Z + Y * Z) - (E(X) + E(Y)) * E(Z)$
$= E(X * Z) + E(Y * Z) - E(X) * E(Z) - E(Y) * E(Z)$
$= E(XZ) - E(X) * E(Z) + E(Y * Z) - E(Y) * E(Z)$
$= Cov(X, Z) + Cov(Y, Z)$

- Generalizza il concetto di varianza
$$Cov(X,X)=Var(X)$$
DIM
$Cov(X, X) = E((X - \mu_X) * (X-\mu_X )) = E((X-\mu_X )^2) = Var(X)$

- SE $X, Y$ indipendenti
$$Cov(X, Y) = 0$$
DIM
$Cov(X, Y) = E(XY) - E(X) * E(Y) = E(X) * E(Y) - E(X) * E(Y) = 0$

$Cov$ misura in modo quantitativo la dipendenza tra due variabili aleatorie quando questa dipendenza c è
Consideriamo la funziona indicatrice di un evento (ATTTTTT diverso da $I_A$ con A insieme) che è una variabile aletoria
$I_A= \begin{cases} 1 \text{ SE A si verifica} \\ 0 \text{ altrimenti} \end{cases}$
Prendendo $A, B\in A$ (algebra), $X=I_A, Y=I_B$
$XY$ sarà essa stessa la funzione indicatrice $= 1$ SE $A\cap B$ si verifica o 0 altrimenti

$E(X) = P(X=1)$
$E(Y) = P(Y=1)$
$E(XY) = P(X=1, Y=1)$
$Cov(X, Y) = E(XY) - E(X) * E(Y) = P(X=1, Y=1) - P(X=1)*P(Y=1)$

SE $Cov(X, Y) > 0, P(X = 1, Y = 1) - P(X = 1) * P(Y = 1) > 0$
P(X = 1, Y = 1) > P(X = 1) * P(Y = 1)
$\frac{P(X = 1, Y = 1)}{P(Y = 1)}>P(X = 1)$
- $P(X = 1 | Y=1) > P(X = 1)$ vuol dire che se so che $Y=1$ allora è piu probabile che anche $X=1$, concetto di relazione di tipo diretta tra due attributi
- $P(X=1 | Y=1) < P(X=1)$ vuol dire che sapere che $Y=1$ mi diminuisce la possibilita che $X=1$, relazione indiretta

OSS $Cov(2X, 2Y) = 4 * Cov(X, Y)$

L'indice di correlazione lineare misura la forza della relazione tra $X$ e $Y$
$$\rho_{X,Y}=\frac{Cov(X,Y)}{\sigma_X*\sigma_Y}$$
È sempre compreso tra $-1$ e $+1$
QUINDI l'indice di correlazione lineare è insensibile alle trasformazioni lineari