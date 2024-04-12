Essendo il supporto un insieme continuo, e quindi anche la variabile aleatoria ho delle difficolta
$P(X = \frac{1}{2}) = 0$ perderebbe senso voler sapere la probabilità di un evento con una probabilita con cosi tante cifre dopo la zero da non essere rilevante
$P(\frac{1}{3} < X < \frac{1}{2})$ ha quindi senso considerare un insieme di valori, eventualmente anche piccolo, che è a sua volta continuo

Con una variabile aleatoria continua consideriamo una funzione di densita di probabilita: quanto è probabile che in un intorno piccolissimo la mia variabile aleatoria assuma quei valori

$$1=P(X \in R)=\int_{-\infty}^\infty f(x) dx$$
SE poniamo $B=[a, b],$ $P(a \leq X \leq b) = \int_a^b f(x) dx$ 
SE poniamo $a=b$, $P(X=a)=\int_a^a f(x) dx$

La relazione che lega la funzione di ripartizione $F$ alla densita $f$ è la seguente
$$F(a)=P(X \in (-\infty, a]) = \int_{-\infty}^a f(x)dx$$
Derivando entrambi i membri: $\frac{d}{da}F(a)=f(a)$
La densita è derivata della funzione di ripartizione

$f_X(x) = k * I_{[0, 1]}(x)$
$P(0 \leq X \leq 1) = 1$
$k = ?$

DIM
SE ho una funzione continua e ne calcolo l'integrale centrato in $a$, si puo approssimare l'integrale con il teorema del valore medio
$$P(a-\frac{\varepsilon}{2} \leq X \leq a+\frac{\varepsilon}{2}) = \int_{a-\frac{\varepsilon}{2}}^{a+\frac{\varepsilon}{2}} f(a) dx \approx \varepsilon *f(a)$$
Quindi la probabilita che $X$ stia in un intorno di $a$ di ampiezza $\varepsilon$ è approssimativamente uguale a $\varepsilon*f(a)$ quindi $f(a)$ rappresenta una indicazione di quanto è probabile che $X$ cada vicino ad $a$
