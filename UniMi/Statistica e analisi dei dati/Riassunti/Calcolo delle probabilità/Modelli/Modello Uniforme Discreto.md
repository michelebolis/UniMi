Il modello uniforme discreto descrive uno spazio equiprobabile di n esiti
$$X\sim U(n)$$
Con $n\in N$ SE $D_X = \{1, …, n\}$
$$f_X(x)=\frac{1}{n}*I_{D_X}(x)$$
$$F_X(x)=P(X \leq x) = \sum_{i <x}P(X=i)$$
SE $n\in N$ e $x \leq n$, $\sum_{i \leq x}P(X=i)=\sum_{i=1}^x P(X=i)=\sum_{i=1}^xf_X(i)=\sum_{i=1}^x\frac{1}{n}=\frac{x}{n}$ 
SE $x \leq n$, $\sum_{i=1}^{\lfloor x \rfloor}\frac{1}{n} = \frac{\lfloor x\rfloor}{n}$
In generale 
$$\sum_{i=1}^{\lfloor x \rfloor}\frac{1}{n} = \frac{\lfloor x\rfloor}{n} * I_{[1,n]}+I_{[n, \infty]}(x)$$
$$F_X(x)=P(X \leq x)= \sum_{i=1}^{\lfloor x \rfloor}\frac{1}{n} = \frac{\lfloor x\rfloor}{n} * I_{[1,n]}+I_{[n, \infty]}(x)$$
es $f_X$ e $F_X$
![[Pasted image 20240411102055.png]]![[Pasted image 20240411102100.png]]

$$E(X) = \frac{n+1}{2}$$
DIM
$E(X) = \sum_{x=1}^n x*f_X(x)=\sum_{x=1}^n x*\frac{1}{n}=\frac{1}{n}*\frac{n*(n+1)}{2}= \frac{n+1}{2}$

$$Var(X)=\frac{n^2-1}{12}$$
DIM
Considerando $Var(X) = E(X^2) - E(X)^2$
$E(X^2) = \sum_{x=1}^n x^2*\frac{1}{n} = \frac{1}{n}*\sum_{x=1}^n x^2 = \frac{1}{n} * \frac{n*(n+1)*(2n+1)}{6}$
$Var(X) = \frac{1}{n}*\sum_{x=1}^n x^2 = \frac{1}{n} * \frac{n*(n+1)*(2n+1)}{6} - \frac{(n+1)^2}{4} =  \frac{n+1}{2}*(\frac{2n+1}{3}-\frac{n+1}{2}) =$
$= \frac{n+1}{2}*\frac{2(2n+1)-3(n+1)}{6}= \frac{n+1}{2}*\frac{n-1}{6} = \frac{n^2-1}{12}$

