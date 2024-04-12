Ripeto l'esperimento Berlunniano in modo indipendente finche non si verifica l esperimento
$$X\sim G(p)$$
Con $p\in (0, 1]$
$X = i$ SE ho fatto esattamente $i$ insuccessi seguiti da un successo, il primo successo avviene esattamente dopo $i\in N\cup\{0\}$ fallimenti
SE $p = 1$, $X = 0$
SE $p = 0$, ciclo infinito

In realta due accezioni:
- Conto il numero di fallimenti (usiamo questa)
- Conto il numero totale di ripetizioni

$f_X(x) = P(X = x)=P(R_1=F\cap R_2= F \cap …\cap R_x=F\cap R_{x+1}=S)$
$f_X(x) = P(R_1 = F) * … * P(R_x = F) * P(R_{x+1} = S) = 1-p * … * 1-p * p = (1-p)^x * p$
$$f_X(x)=(1-p)^x*p*I_{N \cup \{0\}}(x)$$

La funzione di massa somma a 1?
DIM
$\sum_{x=0}^{\infty}f_X(x) = \sum_{x=0}^\infty (1-p)^x*p=p*\sum_{x=0}^\infty (1-p)^x$
Serie geometrica $\sum_{i=0}^\infty a^i$ converge a $\frac{1}{1-a}$ SE E SOLO SE $-1<a<1$
$1 - p$ sta sempre tra 0 e 1
$= p*\frac{1}{1-(1-p)}=p*\frac{1}{p}=1$ DIMOSTRATO

Come grafico per $f_X$ avrò dei bastoncini con $x=1$ sotto $p$ e piano piano ogni bastoncino decresce in modo non lineare

$$F_X(x)=1-(1-p)^{\lfloor x \rfloor +1}$$
DIM
$P(X >m) = \sum_{x>m}p*(1-p)^x=\sum_{x=m+1}^\infty p*(1-p)^x=p*(1-p)^{m+1}*\sum_{x=m+1}^\infty (1-p)^{x-(m+1)}$$= p*(1-p)^{m+1}*\sum_{y=0}^\infty (1-p)^y=p*(1-p)^{m+1}*\frac{1}{1-(1-p)} = (1-p)^{m+1}$
$F_X(x) = P(X \leq x) = 1-P(X>\lfloor x \rfloor) = 1-(1-p)^{\lfloor x \rfloor +1}$

Proprietà
$$P(X \geq n) = P(X > n - 1) = (1 - p)^n$$
Assenza di memoria: tra tutte le distribuzioni discrete il modello geometrico è l unica ad avere tale proprieta
$$P(X \geq i + j | X \geq i) = P(X \geq j)$$
DIM
$P(X \geq i + j | X \geq i) = \frac{P(X>i+j \cap X>i)}{P(X>i)} = \frac{P(X \geq i+j)}{P(X \geq i)} = \frac{(1-p)^{i+j}}{(1-p)^i} = (1-p)^j = P(X \geq j)$
// come se dicessi il ciclo è ancora in esecuzione da $i$ cicli, quale è la probabilita che dopo $j$ cicli


Es $f_X$ e $F_X$
![[Pasted image 20240411105249.png]]![[Pasted image 20240411105253.png]]

---
$$\sum_{i=0}^\infty i*a^i = \frac{a}{(1-a)^2}$$
DIM
$\sum_{i=0}^\infty i*a^i = a*\sum_{i=0}^\infty i*a^{i-1}$
Notando che la derivata di $a^i$ è $i * a^{i-1}$
$= a*\sum_{i=0}^\infty \frac{1}{dx} a^i = a*\frac{1}{dx}*\sum_{i=0}^\infty a^i = a*\frac{1}{dx} (1-a)^{-1} = \frac{a}{(1-a)^2}$

---

$$E(X) = \frac{1-p}{p}$$
DIM
$E(X) = \sum_{x=0}^\infty x*(1-p)^x*p=p*\sum_{x=0}^\infty x*(1-p)^x=p*\frac{1-p}{p^2}= \frac{1-p}{p}$
$$Var(X) = \frac{1-p}{p^2}$$
DIM
$E(X^2) = \sum_{x=0}^\infty x^2*(1-p)^x*p = p*\sum_{x=0}^\infty x^2*(1-p)^x$
$= p*(1-p)*\sum_{x=0}^\infty x^2*(1-p)^{x-1}$
Sapendo che $\frac{d}{dp}-i*(1-p)^i=-i^2*(1-p)^{i-1}$
$= p*(1-p)*\sum_{x=0}^\infty \frac{1}{dp}-x*(1-p)^x$
$= p*(1-p)*\frac{1}{dp} \sum_{x=0}^\infty -x*(1-p)^x$
Sapendo che $\sum_{i=0}^\infty i*a^i=\frac{a}{(1-a)^2}$
$=-p * (1-p)*\frac{1}{dp}\frac{1-p}{p^2} = -p*(1-p)*\frac{p-2}{p^2}=(1-p)*\frac{2-p}{p^2}$
$Var(X) = E(X^2)-E(X)^2 = (1-p)*\frac{2-p}{p^2}-\frac{(1-p)^2}{p^2} = \frac{1-p}{p^2}*(1-p-1+p)=\frac{1-p}{p^2}$