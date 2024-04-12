Consideriamo il modello uniforme discreto, aumentando n arrivando ad un insieme infinito
MA se considero un numero infinito di punti, $f_X$ diventa sempre $= 0$

Invece di considerare $N+1$ punti, consideriamo $N+1$ valori equi spaziati tra 0 e 1
Avrò cosi ancora $N+1$ punti
$0, \frac{1}{N},...,\frac{N-1}{N}, 1$

Ho cosi un insieme limitato
Facendo andare all'infinito $N$, se considero $F_X$ (funzione a gradini con $N+1$ gradini di altezza $\frac{1}{N+1}$), 
- per $x < 0$ sarà nulla
- per $x \geq 1$ sarà $y = 1$
- mentre tra 0 e 1 si comporterà come la bisettrice

Per essere una funzione di ripartizione:
- Deve essere non negativa
- Il $\lim_{x->\infty}$ deve essere 1
- Deve essere monotona crescente e continua 
MA quindi questa $F_X$ rispetta le condizioni della funzione di ripartizione

Essendo il supporto un insieme continuo, e quindi anche la variabile aleatoria ho delle difficolta
$P(X = \frac{1}{2}) = 0$ perderebbe senso voler sapere la probabilità di un evento con una probabilita con cosi tante cifre dopo la zero da non essere rilevante
$P(\frac{1}{3} < X < \frac{1}{2})$ ha quindi senso considerare un insieme di valori, eventualmente anche piccolo, che è a sua volta continuo

Con una variabile aleatoria continua consideriamo una funzione di densita di probabilita: quanto è probabile che in un intorno piccolissimo la mia variabile aleatoria assuma quei valori

$f_X(x) = k * I_{[0, 1]}(x)$
$P(0\leq X \leq 1) = 1$
$k = ?$

DIM
SE ho una funzione continua e ne calcolo l'integrale centrato in $a$
$\int_{a-\frac{\varepsilon}{2}}^{a+\frac{\varepsilon}{2}} f(a) dx \approx \varepsilon *f(a)$
$P(a-\frac{\varepsilon}{2} \leq X \leq a+\frac{\varepsilon}{2})$
$$P(a \leq X \leq b) = \int_a^b f_X(x)dx$$
Richiesta per la fX:
- Non deve essere negativa
- $\int_{-\infty}^{+\infty} f_X(x)dx=1$

DIM  
$1=\int_{-\infty}^{+\infty}f_X(x) dx = \int_0^1 k dx =  k*\int_0^1 dx =k$
$$k = 1$$
$$X\sim U([0, 1])$$

$P(a < X < b) = F_X(b) - F_X(a) = b - a$ 
OSS estremi non contano perche integrale indifferente dal fatto che l intervallo sia aperto o chiuso

"DIM" $P(a \leq X \leq b) = P(a < X \leq b) + P(a) = P(a < X \leq b) + 0 = P(a < X \leq b)$

---
$F_X(x)=\int_{-\infty}^xf_X(u) du$
$\lim_{x->-\infty}F_X(x)=0$

Teorema fondamentale del calcolo integrale: l operatore di integrale e derivata sono uno l'inverso di un altro
SE derivo $F_X$, devo ottenere la funzione di densita
$x dx = 1$

---

$E(X) = \int_{-\infty}^{+\infty}x*f_X(x) dx$
$$E(g(X)) = \int_{-\infty}^{+\infty}g(x)*f_X(x) dx$$
Continua a valere che SE $X \geq 0$
$E(X) = \int_0^\infty 1-F_X(x)dx$

Riguardando Markov pensiamo a cosa dobbiamo cambiare per una variabile continua (sostituiamo sommatorie con integrale)

NON dobbiamo riguardare dimostrazione di Chebyshev perche si basa su Markov