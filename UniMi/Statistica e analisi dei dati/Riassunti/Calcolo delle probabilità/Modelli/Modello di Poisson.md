Il modello di Poisson considera un modello binomiale in cui $n$ cresce in modo indefinito e $p$ decresce
$n$ cresce e $p$ decresce, $np = \lambda$ 
$$X \sim P(\lambda)$$
$$\binom{n}{x}*p^x*(1-p)^{(n-x)}= \frac{n!}{x!*(n-x)!}*p^x*(1-p)^{(n-x)}$$
$$= \frac{n*(n-1)*...*(n-x+1)*(n-x)!}{x!*(n-x)!}*\frac{\lambda^x}{n^x}*(1-\frac{\lambda}{n})^{{n-x}}$$
Sopra la frazione mi rimangono $x$ fattori, come anche $n^x$
$$\frac{n*(n-1)*...*(n-x+1)}{n*...*n}*\frac{\lambda^x}{x!}*\frac{(1-\frac{\lambda}{n})^n}{(1-\frac{\lambda}{n})^x}$$
$$\frac{n*(n-1)}{n*n}*\frac{n-x+1}{n}*\frac{\lambda^x}{x!}*\frac{(1-\frac{\lambda}{n})^n}{(1-\frac{\lambda}{n})^x}$$
Per $n->\infty$
$$= 1*1*\frac{\lambda^x}{x!}*\frac{(1-\frac{\lambda}{n})^n}{1}$$
Ricordando che $e = \lim_{n->\infty}(1+\frac{1}{n})^n$ e che $e^\alpha = \lim_{n->\infty}(1+\frac{\alpha}{n})^n$
$$= e^{-\lambda}*\frac{\lambda^x}{x!}$$
Vantaggio: risparmio computazione
$$f_X(x)=e^{-\lambda}*\frac{\lambda^n}{x!} * I_{N \cup \{0\}}(x)$$

Estensione della binomiale in cui non ho piu un numero fissato di ripetizioni, o in generale un numero molto grande, posso approssimare

Per essere la funzione di massa di probabilità:
- Deve sommare a 1
$\sum_{x=0}^\infty e^{-\lambda}*\frac{\lambda^x}{x!} = e^{-\lambda}*\sum_{x=0}^\infty \frac{\lambda^x}{x!}$
Sviluppo di Taylor centrato in 0 di $e^\lambda$
$=e^{-\lambda} * e^\lambda  =1$
- Non può essere negativa: essendo il prodotto di due valori sempre positivi, non ci sono problemi

ATT per calcolare $E(X)$ non posso fare il limite del valore atteso della binomiale, il numero andrebbe ad infinito
La distribuzione di Poisson ha $$E(X) = Var(X) = \lambda$$
DIM
$E(X) = \sum_{x=0}^\infty x*e^{-\lambda}*\frac{\lambda^x}{x!} = e^{-\lambda}*\sum_{x=1}^\infty \frac{\lambda^x}{(x-1)!}$
$=\lambda*e^{-\lambda}*\sum_{x=1}^\infty \frac{\lambda^{(x-1)}}{(x-1)!}$
Considerando $y=x-1$
$=\lambda*e^{-\lambda}*\sum_{y=0}^\infty \frac{\lambda^{y}}{y!}$
$=\lambda*e^{-\lambda}*e^{\lambda}=\lambda$

$E(X^2) = \sum_{x=0}^\infty x^2*e^{-\lambda}*\frac{\lambda^x}{x!} = e^{-\lambda}*\sum_{x=1}^\infty x*\frac{\lambda^x}{(x-1)!}$
Considerando $y=x-1$
$=\lambda*e^{-\lambda}*\sum_{y=0}^\infty (y+1) \frac{\lambda^{y}}{y!}$
$=\lambda*\sum_{y=0}^\infty (y+1) *e^{-\lambda} \frac{\lambda^{y}}{y!}$
Sapendo che $f_Y(y) = e^{-\lambda}*\frac{\lambda^y}{y!}$
$= \lambda*\sum_{y=0}^\infty (y+1)*f_Y(y)=\lambda*E(y+1)$

$E(X^2) = \lambda*E(y+1)$ MA SE $Y \sim P(\lambda)$
$= \lambda*(\lambda+1)=\lambda^2+\lambda$
$Var(X) = E(X^2)-E(X)^2=\lambda^2+\lambda-\lambda^2=\lambda$

ATT non è detto che se va bene l'approssimazione per questo evento non va bene per un altro evento
Per verificare bontà dell'approssimazione globalmente
- Rapporto tra le funzioni di massa --> difficile
- Sovrappongo i grafici