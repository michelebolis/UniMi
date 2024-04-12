La varianza campionaria è uno stimatore non distorto per la varianza

Popolazione $X\sim F(\Theta),\tau(\Theta)$ quantita da stimare dato un campione $X_1, …, X_n$
$$S^2=\frac{1}{n-1}*\sum_{i=1}^n(X_i-\overline X)^2$$
$$E(S^2)=\sigma^2=Var(X)$$
DIM
- Passo 1: guardando la sommatoria
$\sum_{i=1}^n(X_i-\overline X)^2 = \sum_{i=1}^nX_i^2-2X_i\overline X+\overline X^2=\sum_{i=1}^n X_i^2-2\overline X*\sum_{i=1}^n X_i+\sum_{i=1}^n \overline X^2 = \sum_{i=1}^n X_i^2-n\overline X^2$
- Passo 2: per il calcolo della varianza, uso formula alternativa $E(X^2) = Var(X) + E(X)^2$
- Passo 3: sapendo che

$E(\overline X) = E(X) = \mu$
$Var(\overline X) = \frac{\sigma}{n}$

- Passo 4

$(n-1)*S^2=\sum_{i=1}^n(X_i-\overline X)^2$
$(n-1)*S^2=\sum_{i=1}^n X_i^2-n\overline X^2$
$(n-1)*S^2 = \sum_{i=1}^n E(X_i^2)-nE(\overline X)^2$
$(n-1)*S^2 = \sum_{i=1}^n Var(X_i)+E(X_i)^2-n(Var(\overline X)+E(\overline X)^2)$
$(n-1)*S^2 = \sum_{i=1}^n Var(X_i)+\sum_{i=1}^n E(X_i)^2-n(Var(\overline X)+E(\overline X)^2)$
$(n-1)*S^2 =nVar(X)+nE(X)^2-n(\frac{\sigma^2}{n})-nE(X)^2$
$(n-1)*S^2 =n\sigma^2-\sigma^2$
$(n-1)*S^2 =\sigma^2*(n-1)$
$S^2=\sigma^2$

Si mette n-1 per garantire che lo stimatore sia non deviato