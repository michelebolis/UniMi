es scelta tra due stimatori non distorti
$X \sim U([0,\Theta]),\tau(\Theta)=\Theta$
- $T''$

$E(\overline X)=E(X)=\frac{\Theta}{2}\neq \Theta$ 
$2E(\overline X)=\Theta$
Uso proprieta di linearità al contrario, $E(2\overline X) = \Theta$ QUINDI $T'' = 2\overline X$

SE ho una stimatore non distorto per qualcos'altro, sfruttando le proprieta del valore atteso, ottenere uno stimatore non distorto per quello che mi interessa? NON è possibile usare proprieta del valore atteso
Ottengo uno stimatore MA che avra probabilmente un bayes

- $T'$

Siccome $\Theta$ è l'estremo destro, potrei prendere il max della popolazione
$T' = \max_{1 <= i <= n} (X_i)$
$F_{T'}(x) = P(T' \leq x) = P(\max_{1 <= i <= n }X_i \leq x) = P(\forall i = 1, .., n, X_i \leq x) =$
$P(\bigcap_{i=1}^n X_1 \leq x) = \prod_{i=1}^n P(X_i \leq x) = \prod_{i=1}^n F_{X_i}(x) = \prod_{i=1}^n F_{X}(x) = F_{X}(x)^n$
//da $F_{X_i}$ a $F_{X}$ perche le variabili aleatorie del campione seguono la stessa legge della popolazione
Guardando il grafico, $F_X(x) = \frac{x}{\Theta}$
$=(\frac{x}{\Theta})^n$
$$f_{T'}(x)=F_{T'}(x')=\frac{d}{dx} (\frac{x}{\Theta})^n=n*(\frac{x}{\Theta})^{n-1}*\frac{1}{\Theta}=\frac{n*x^{n-1}}{\Theta^n}$$
$$E(T')=\int_0^\Theta x*f_{T'}(x)dx=\int_0^\Theta x*\frac{n*x^{n-1}}{\Theta^n} = \frac{n}{\Theta^n}*\int_0^\Theta x^n dx=$$$$=\frac{n}{\Theta^n}*(\frac{x^{n+1}}{n+1}|_0^\Theta) = \frac{n}{\Theta^n}*\frac{\Theta^{n+1}}{\Theta+1} = \frac{n*\Theta}{n+1}$$
$T' = \max X_i$
$E(T') = \frac{n}{n+1}*\Theta$
È distorto
$T'=\frac{n+1}{n}*\max X_i \implies E(T')=\Theta$ 

Ora abbiamo quindi due stimatori non distorti per il valore atteso, $T'$ e $T''$
SE entrambi sono consistenti, si puo fare un confronto puntuale
- MSE

$MSE(T')=Var(T')=Var(\max X_i)=E((\frac{n+1}{n}*\max X_i)^2)-E(T')^2=(\frac{n+1}{n})^2*E(T'^2)-E(T')^2$
$f'_{T'}(x)=\frac{n*x^{n-1}}{\Theta^n}$
$E(T')=\Theta$
$$E(T'^2) = \int_0^\Theta x^2*\frac{n*x^{n-1}}{\Theta^n} dx = \frac{n}{\Theta^n}*\int_0^\Theta  x^{n+1}dx=$$$$= \frac{n}{\Theta^n}*(\frac{x^{n+1}}{n+1}|_0^\Theta) = \frac{n}{\Theta^n}*\frac{\Theta^{n+2}}{\Theta+2} = \frac{n}{n+2}*\Theta^2$$$$MSE(T')=(\frac{n+1}{n})^2*\frac{n}{n+2}*\Theta^2-\Theta^2=\Theta^2*(\frac{n+1}{n})^2*\frac{n}{n+2})$$
$$=\Theta^2*(\frac{n^2+2n+1-n^2-2n}{n*(n+2)})=\frac{\Theta^2}{n*(n+2)}$$

È consistente? $\lim_{n->\infty}\frac{\Theta^2}{n*(n+2)} = 0$ SI

$$MSE(T'')=Var(T'')=Var(2\overline X)=\frac{4Var(X)}{n}=\frac{4}{n}*\frac{\Theta^2}{12}=\frac{\Theta^2}{3n}$$
È consistente? $\lim_{n->\infty}\frac{\Theta^2}{3n}=0$ SI

- Confronto MSE

Ho quindi 2 MSE: dovremmo preferire $T'$ perche tende a 0 piu velocemente e perche per un $n$ fissato,
$MSE(T')\leq MSE(T'')$
$\frac{\Theta^2}{n*(n+2)} \leq \frac{\Theta^2}{3n}$
$3\leq n+2$
$n\geq  1$
QUINDI $T'$ ha un MSE minore sempre e quindi avro un errore medio piu basso

Passi:
- Data la quantità di interesse --> metodo plug in per ottenere degli stimatori
- Faccio in modo che non siano distorti con le proprieta del valore atteso
- Verifico la consistenza con MSE
- Confronto i 2 MSE