Sia $X$ variabile aleatoria con $E(X) = \mu \in R$ e la $Var(X)=\sigma^2 R^+$ finiti

$$\forall r \geq 0, P(|X-\mu|\geq r) \leq \frac{\sigma^2}{r^2} $$
La probabilità che il valore assunto dalla variabile aleatoria disti piu di $r$ dal valore atteso
DIM
$|X - \mu| \geq r \iff (X - \mu)^2 \geq r^2$
Gli eventi si coimplicano --> le probabilità sono uguali
$P( (X - \mu)^2 \geq r^2 )$ 
$Y=(X-\mu )^2$ //rispetta le specificazioni di Markov
$P(Y \geq r^2) \leq \frac{E(Y)}{r^2}$
$E(Y) = E((X - \mu )^2) = E(\sigma^2)$
$P(Y \geq r^2) \leq \frac{\sigma^2}{r^2}$  DIMOSTRATO

SE $r$ aumenta, denominatore cresce rapidamente, ragionevolmente l evento diventa meno probabile perché mi sposterò molto dal valore atteso

Indichiamo $r = k * \sigma$ con $k>0$
$P(|X - \mu | \geq k * \sigma ) \leq \frac{\sigma^2}{(k+\sigma)^2}=\frac{1}{k^2}$

Otteniamo che la probabilità che una variabile aleatoria differisca dal suo valore atteso per piu di $k$ volte la deviazione standard, non può superare il valore $\frac{1}{k^2}$