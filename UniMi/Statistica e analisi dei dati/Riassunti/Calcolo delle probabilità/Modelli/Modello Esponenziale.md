$\frac{p}{\lambda}*x_i$ con $\lambda>0$ e $0<p<1$
Moltiplicando per $p$ riduco $x_i$ come anche dividere per $\lambda$
Al limite per $p -> 0$, i bastoncini del grafico si toccano ottenendo una curva decrescente che dipende solo da $\lambda$
$$f_X(x) = \lambda * e^{-\lambda x}*I_{[0,\infty]}(x)$$
$$X\sim E(\lambda)$$
La curva descresce da $(0, \lambda)$ verso $y=0$ all'aumentare di $x$
Verificare che $f_X$ sia una funzione di densita
- È non negativa
- $\int_{-\infty}^{+\infty}f_X(x) dx=\int_{-\infty}^{+\infty} \lambda * e^{-\lambda x}dx=\int_0^{+\infty} \lambda * e^{-\lambda x}dx$
Considerando che $((e^{-\lambda x})^{-1})'=-\lambda * e^{-\lambda x}$
$= -e^{-\lambda x}|^\infty_0=1$

$$F_X(x)=(1-e^{-\lambda x})*I_{[0,\infty]}(x)$$
DIM
$F_X(x) = \int_0^x \lambda * e^{-\lambda u} du$
Poniamo $v=\lambda u$ quindi $dv=\lambda du$
$=\int_0^{\lambda x}e^{-v}dv=-e^{-v}|_0^{\lambda x}=-e^{-\lambda x}+1=1-e^{-\lambda x}$

es $f_X$ e $F_X$
![[Pasted image 20240411131750.png]]
![[Pasted image 20240412111900.png]]
$$E(X)=\frac{1}{\lambda}$$
DIM
$E(X)=\int_0^\infty x*\lambda *e^{-\lambda x} dx=$
Integrazione per parti $\int f(x)*g'(x)dx=f(x)*g(x)-\int f'(x)*g(x)$
Integro per parti considerando $g'(x)=\lambda * e^{-\lambda x}$ e $f(x)=x$, con $g(x)=e^{-\lambda x}$
$-x*e^{-\lambda x}|_0^{+\infty}+\int_0^{+\infty} e^{-\lambda x}dx=0+\frac{1}{\lambda}*\int_0^{+\infty}\lambda *e^{-\lambda x} dx=  \frac{1}{\lambda}*\int_0^{+\infty}f_X(x)dx=\frac{1}{\lambda}$

$$Var(X)=\frac{1}{\lambda ^2}$$
DIM
$E(X^2)=\int_0^{+\infty}x^2*e^{-\lambda x}dx=x^2*-e^{-\lambda x} |_0^{+\infty}+\lambda *\int_0^\infty \lambda * e^{-\lambda x} dx$
$=\frac{2}{\lambda}*\int_0^\infty \lambda*\lambda*e^{-\lambda x} dx=\frac{2}{\lambda}*\int_0^\infty \lambda*f_X(x)dx=\frac{2}{\lambda}*\frac{1}{\lambda}=\frac{2}{\lambda^2}$
$Var(X)=E(X^2)-E(X)^2=\frac{2}{\lambda^2}-\frac{1}{\lambda^2}=\frac{1}{\lambda^2}$

Proprietà
- Assenza di memoria
$P(X>s+t|X>t)=P(X>s)$
`DIM`
$\frac{P(X>(s+t) \cap X>t)}{P(X>t)}=P(X>s)$
OSS $P(X>(s+t)) = P(X>s)*P(X>t)$
OSS $P(X>t) = 1-F_X(t)=1+1+e^{-\lambda t} =e^{-\lambda t}$ 
$e^{-\lambda*(s+t)}=e^{-\lambda* s}*e^{-\lambda* t}$

- $\lambda$ descrive il modello quindi cambiando $\lambda$ cambia il modello

$X \sim E(\lambda), c>0, Y=cX$
$F_Y(x) = P(Y\leq x) = P(c*X \leq x) = P(X \leq \frac{x}{c}) = F_X(\frac{x}{c}) = 1-\frac{e^{-\lambda*x}}{c} = 1-\frac{e^\lambda}{c} * x$
Ponendo $\lambda' = \frac{\lambda}{c}$
$=1-c*e^{-\lambda'}$
QUINDI $Y \sim E(\frac{\lambda}{c})$

- Il piu piccolo dei valori assunti per una serie di variabili aleatorie

$X_1, ..., X_n, Y=\min_{i=1,...,n}X_i$
$\forall i, X_i \sim E(\lambda_i)$ e $X_i$ indipendente
$P(Y>z)=P(\min X_i>x)=P(\bigcap_{i=1}^n X_i>x)=\prod_{i=1}^nP(X_i>x)$ //Essendo indipendenti
$F_Y(x)=1-\prod_{i=1}^n P(X_i>x)=1-\prod_{i=1}^n 1-F_{X_i}(x)$

Questo vale per qualsiasi distribuzione
Sapendo che è esponenziale
$1-\prod_{i=1}^ne^{-\lambda_ix}= 1-e^{\prod_{i=1}^n -\lambda_ix}$
Considero $\lambda'=\prod \lambda_i$
$= 1-e^{-\lambda'x}$

SE ho $n$ variabili aleatoria esponenziali ognuna con un suo parametro, il minimo tra le variabili aleatorie segue anche esso una distribuzione esponenziale con parametro dato dalla produttoria dei parametri

