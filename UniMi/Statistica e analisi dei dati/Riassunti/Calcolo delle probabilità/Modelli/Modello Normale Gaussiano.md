$$X \sim G(\mu, \sigma)$$
Con $\mu \in R, \sigma \in R^+$
$$f_X=\frac{1}{\sqrt{2\pi}\sigma}*e^{-\frac{1}{2}(\frac{(x-\mu)^2}{\sigma^2})}$$
Non essendoci la funzione indicatrice, il supporto è $R$
Studio di funzione:
- Questa funzione non sarà mai uguale a 0
- $\lim_{x->\infty}$ la funzione va a 0 (dall'alto)
- Derivata prima:
$$f'_X(x)=\frac{1}{\sqrt{2\pi}\sigma}*e^{-\frac{1}{2}(\frac{(x-\mu)^2}{\sigma^2})}*(\frac{1}{2}*\frac{2}{\sigma^2}*(x-\mu))=\frac{1}{\sqrt{2\pi\sigma^3}}*(\mu-x)*e^{-\frac{1}{2}(\frac{(x-\mu)^2}{\sigma^2})}$$
Quando $f'_X(x)>0$
$\frac{-(x-\mu)}{\sigma^2}>0 \iff x-\mu<0 \iff x<\mu$
QUINDI la funzione cresce fine a $\mu$ e poi decresce

- Derivata seconda

$$f''_X(x)=\frac{1}{\sqrt{2\pi\sigma^3}}*(e^{-\frac{1}{2}(\frac{(x-\mu)^2}{\sigma^2})}+(\mu-x)*e^{-\frac{1}{2}(\frac{(x-\mu)^2}{\sigma^2})})*(-\frac{1}{2}*2*\frac{x-\mu}{\sigma^2})$$
$$=-\frac{1}{\sqrt{2\pi\sigma^3}}*(e^{-\frac{1}{2}(\frac{(x-\mu)^2}{\sigma^2})})*(1-\frac{(x-\mu)^2}{\sigma^2})$$
Quando $f''_X(x)>0$
$\frac{(x-\mu)^2}{\sigma^2}>1 \iff |\frac{x-\mu}{\sigma}|>1$
$|x-\mu|>\sigma$ //perché so che $\sigma>0$
$x-\mu>\sigma \iff x>\pi+\sigma$
$x-\mu<-\sigma \iff x<\pi-\sigma$

QUINDI
- $(-\infty, \mu-\sigma]$ crescente e convessa verso l alto
- $(\mu-\sigma,\mu]$ cresce ma con concavità verso il basso
- $(\mu, \mu+\sigma)$ decresce con concavità verso il basso
- $(\mu+\sigma, +\infty)$ decresce con concavità verso l alto

Si puo dimostrare che se invece di $\frac{1}{\sqrt{2\pi}\sigma}$ metto un $\alpha$, l unico modo per far integrare tutto a 1 è $\alpha=\frac{1}{\sqrt{2\pi}\sigma}$

Non esiste una forma analitica per l'integrale per questa funzione
$$F_X(x) =\int_{-\infty}^x \frac{1}{\sqrt{2\pi}\sigma}*e^{-\frac{1}{2}(\frac{(u-\mu)^2}{\sigma^2})} du= ???$$
$$E(X)=\mu$$
Dato che nel grafico è centrale E perche la distribuzione è simmetrica
SE distribuzione simmetrica rispetto ad un asse, il valore atteso sarà il valore dell'asse

$\sigma$ è legato alla dispersione intorno al valore atteso, infatti i flessi sono distanziati $\sigma$ da $\mu$
$$Var(X)=\sigma^2$$
Piu la distanza, quindi $\sigma$ diminuisce, allora il grafico sale perche l integrale di tutto deve fare 1
Sull'asse delle ordinate non so dove è 1, infatti SE $\sigma$ piccolissimo, l'ordinata del picco va verso infinito
MA come faccio a calcolare le probabilità se non posso calcolare l'integrale in forma analitica? Bisogna guardare la tabella 
$P(X\in A)=\int_A f_X(x)dx$
Questa espressione dipende da $x, \mu$ e $\sigma$

Proprietà
- Trasformazione lineare

Data $X \sim G(\mu,\sigma)$
$Y=aX+b$, con $a,b\in R$
$Y \sim G(a*\mu+b, |a|*\sigma)$

- Riproducibilità

$X_1, ..., X_n$ indipendenti, posso ragionare con $X_i \sim G(\mu_i,\sigma_i)$
$Y=\sum_{i=1}^n X_i, Y\sim G(?,?)$
$$E(Y)=E(\sum_{i=1}^n X_i)=\sum_{i=1}^n E(X_i) = \sum_{i=1}^n \mu_i$$
ATT posso fare la stessa cosa di sopra SOLO con la indipendenza
$$Var(Y)=Var(\sum_{i=1}^nX_i)=\sum_{i=1}^nVar(X_i)=\sum_{i=1}^n\sigma_i^2$$
$$Y \sim G(\sum_{i=1}^n\mu_i,\sum_{i=1}^n\sigma_i^2)$$

Gaussiana standard 
Standardizzazione: $Z=\frac{X-\mu}{\sigma}$
$$E(Z) = 0$$
$$Var(Z)=1$$
$$Z \sim G(0,1)$$
Indipendentemente dal modello di distribuzione della variabile aleatoria, ottengo una variabile aleatoria con $E(X) = 0$ e $Var(X) = 1$ (spesso cambiando specificazioni cambia il tipo di modello della variabile aleatoria)
DIM
$E(Z)=E(\frac{X-\mu}{\sigma})=\frac{1}{\sigma}*E(X-\mu)=\frac{1}{\sigma}*(E(X)-\mu)=0$
$Var(Z)=Var(\frac{X-\mu}{\sigma})=\frac{1}{\sigma^2}*Var(X-\mu)=\frac{1}{\sigma^2}*Var(X)=1$

Dato $X \sim G(\mu, \sigma)$
$$F_X(x)=P(X\leq x)=P(\frac{X-\mu}{\sigma}\leq\frac{x-\mu}{\sigma}) = P(Z\leq \frac{x-\mu}{\sigma})=F_Z(\frac{x-\mu}{\sigma})=\Phi(\frac{X-\mu}{\sigma})$$
QUINDI basta avere una sola tabulazione, la tabulazione della normale standard
Per l importanza della gaussiana normale standard la sua $F$ viene indicata con $\Phi$

Mediana di una distribuzione gaussiana $= E(X)$

Si puo estendere la mediana ai quantili $x_q$ con $q \in (0, 1)$
$P(X <= x_q) = q$

Diagramma Q-Q
Lo avevamo usato per verificare se due campioni erano dello stesso esperimento confrontando i punti formati dai percentili
Possiamo fare la stessa cosa per due variabili aleatorie, verificando se hanno una stessa distribuzione confrontando i quantili empirici con i quantili teorici, segnando i punti e confrontando con la bisettrice
Potrei non specificare la distribuzione ma considerando le due variabili come legge gaussiana