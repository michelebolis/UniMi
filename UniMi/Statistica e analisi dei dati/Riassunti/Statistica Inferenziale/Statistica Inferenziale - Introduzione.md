Statistica inferenziale: da un informazione parziale di un campione vogliamo indurre una caratteristica generale del campione
Popolazione: $X \sim F$ con $D_X$ ($F$ una distribuzione qualsiasi che non conosciamo)
Campione: $X_1, …, X_n$ successione di variabili aleatorie che sono identicamente distribuite come X E devono essere indipendenti (quindi $\forall i, X_i \sim F$, QUINDI $E(X_i) = E(F)$) si scrive $\frac{id}{\sim}F$
mentre $x_1, …, x_n$ sono i valori che ho ottenuto dai campioni

SE $F$ completamente sconosciuta: statistica inferenziale non parametrica
SE so che $F$ segue una legge ma non ne conosco i parametri: statistica inferenziale parametrica
Stima
- Puntuale: voglio trovare il parametro preciso della legge, $\Theta = ?$
- Per intervalli

Introduciamo la statistica/stimatore per approssimare i campioni nella stima
Avendo accesso ad un informazione parziale tramite un campione $X_1, …, X_n$ i.i.d. e $\forall i, X_i \sim F(\Theta)$
Una statistica è una trasformazione $t: D_{X^n} -> R$
$t(x_1, …, x_n) = \hat{\Theta}$ //^ sta ad indicare la stima
$t(x_1, …, x_n) \approx \Theta$
Introduciamo una statistica $T = t(X_1, …, X_n)$, che è una variabile aleatoria che non dipende da nessun parametro ignoto
Le specificazioni di $T$ saranno $\hat{\tau}$

Considerando $X \sim E(\lambda),\lambda=\Theta,E(X)=\frac{1}{\lambda}=\tau(\lambda)$
Consideriamo $\tau(\Theta)$ una quantità di interesse che dipende da $\Theta$
Sara plausibile che la caratteristica della popolazione a cui sono interessato dipenderà da $\Theta$ e quindi sarà anch'essa sconosciuta come $\Theta$
$t(x_1, …, x_n) =\hat{\tau}$ 
$t(x_1, …, x_n)\approx\tau(\Theta)$

Ma che statistica utilizzo?
$\Theta \in N$
$f_X(x)=I_{[\Theta-\frac{1}{2}, \Theta+\frac{1}{2}]}(x)$
Mi basta un campione di un elemento per trovare $\Theta$
$X_1, t(x_1) = int(x_1)$ //intero piu vicino
MA l'intero piu vicino sarà $\Theta, t(x_1) = \Theta$