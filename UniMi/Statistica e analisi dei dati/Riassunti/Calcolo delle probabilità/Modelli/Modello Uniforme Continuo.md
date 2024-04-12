[[Modello Uniforme Continuo - Introduzione]]
$$X \sim U([a,b])$$
$$f_X(x) = \frac{1}{b-a}*I_{[a,b]}(x)$$
Requisiti:
- Sicuro è non negativa
- Funzione di densita somma a 1?
DIM
$$\int_{-\infty}^{+\infty}f_X(x)dx=\int_a^b \frac{1}{b-a}dx=\frac{1}{b-a}\int_a^b dx = \frac{1}{b-a}*(b-a)=1$$

$$F_X(x)=\frac{x-a}{b-a}*I_{[a,b]}(x)+I_{(b,\infty)}(x)$$
DIM
$F(X)=P(X\leq x)=\int_a^x f_X(x)du = \int_a^x \frac{1}{b-a}du=\frac{1}{b-a}\int_a^x du = \frac{x-a}{b-a}$

es $f_X$ e $F_X$
![[Pasted image 20240411125705.png|300]]![[Pasted image 20240411125711.png]]

$E(X)$ rappresenta la centralità
$$E(X)=\frac{a+b}{2}$$
DIM modo 1
$E(X)=\int_a^b x*f_X(x)dx=a+b+\frac{a}{2}=\frac{a+b}{2}$
DIM modo 2
$E(X) = \int_a^b x*\frac{1}{b-a} dx = \frac{1}{b-a} *  \int_a^b x dx = \frac{1}{b-a} *\frac{x^2}{2}|^b_a$
$=\frac{1}{b-a} * (\frac{b^2-a^2}{2})  = \frac{1}{b-a}*\frac{(b-a)*(b+a)}{2}=\frac{b+a}{2}$

$$Var(X)=\frac{(b-a)^2}{12}$$
DIM
$E(X^2)\int_a^b x^2*f_X(x) dx = \int_a^b x^2 *\frac{1}{b-a} dx = \frac{1}{b-a} * \int_a^b x^2 dx = \frac{1}{b-a} *  \frac{x^3}{3}|_a^b$
$=\frac{1}{b-a} * \frac{b^3-a^3}{3}=\frac{1}{b-a}*\frac{(b-a)*(a^2+ab+b^2)}{3}=\frac{a^2+ab+b^2}{3}$
$Var(X)=E(X^2)-E(X)^2=\frac{b^2+ab+b^2}{3}+\frac{-a^2-2ab-b^2}{4}$
$\frac{4a^2+4ab+4b^2-3a^2-6ab-3b^2}{12}=\frac{a^2-2ab+b^2}{12}=\frac{(b-a)^2}{12}$

La varianza rappresenta la dispersione rispetto al valore atteso, infatti la varianza è legata all'ampiezza dell'intervallo

Quantile q-esimo ($q \in [0,1]$) di v.a. $X$ è $x*q \in D_X$ t.c. $P(X \leq x*q) = q$
$x*q = F_X^{-1}(q)$ MA fallace SE $F_X$ non è invertibile
- SE continua, posso sempre farlo
- SE discreta, è un casino, dipende dove mi posiziono con q

Posso quindi parlare della mediana di una variabile aleatoria
(modello uniforme continua la mediana sarà $E(X)$)