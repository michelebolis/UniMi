Consideriamo $X, Y$ congiuntamente
Estendiamo la funzione di ripartizione alla funzione di ripartizione congiunta di $X$ e $Y$
$F_{X, Y}(x, y) = P(X \leq \{x\} \cap Y \leq \{y\})$
$\lim_{y->\infty}F_{X,Y}(x,y)=\lim_{y->\infty}P(X\leq x, Y \leq y) = P(X \leq x) = F_X(x)$
Funzione di ripartizione marginale quando ottengo una funzione di ripartizione da una funzione di ripartizione congiunta

Funzione di massa di probabilità congiunta di $X$ e $Y$: 
$$f_{X, Y}(x, y) = P(X = x, Y = y)$$
$$\sum_{x_i \in D}f_{X, Y}(x, y) = \sum_{x_i \in D}P(X = x, Y = y)$$
Fissato $j$, gli $x_i$ saranno disgiunti
$$=P(\bigcup_{x_i \in D}\{X=x_i, Y=y_i\}) = P(Y=y_i)=f_Y(y_i)$$

Indipendenza tra due variabili aleatorie $X$ e $Y$
$X$ e $Y$ sono indipendenti SE E SOLO SE $\forall A, B \subseteq R, P(X \in A, Y \in B) = P(X \in A)*P(Y \in B)$
`DIM` ($\implies$)
SE $X$ e $Y$ sono indipendenti ALLORA $f_{X, Y}(x, y) = f_X(x) * f_Y(y), \forall x, y$
$X, Y$ indipendenti $\implies \forall x, y, \{x\} \in R$ e $\{y\} \subseteq R \implies$ 
$P(X \in \{x\}, Y \in \{y\})= P(X \in \{x\})*P(Y \in \{y\}) = P(X=x, Y=y) = P(X=x)*P(Y=y)$

`DIM` ($\impliedby$)
$\forall x, y, f_{X, Y}(x, y) = f_X(x)*f_Y(y) \implies A={x_{a_1}, x_{a_2}, …}$ e $B={x_{b_1}, …} \implies$
$P(X \in A, Y \in B) = \sum_{x \in A} \sum_{y \in B} P(X=x, Y=y) = \sum_{x \in A} \sum_{y \in B} f_{X, Y}(x, y) =$
$\sum_{x \in A} \sum_{y \in B} f_X(x)*f_Y(y) = \sum_{x \in A} f_X(x) * \sum_{y \in B} f_Y(y) = P(X \in A) * P(X \in B)$
Ho ottenuto indipendenza tra insiemi

Si può generalizzare per una sequenza di variabili aleatorie
$X_1, …, X_n$ sono indipendenti SE E SOLO SE $\forall A_1, …, A_n \subseteq R,$
$$P(\bigcap_{i=1}^n\{X_i \in A\})=\prod_{i=1}^nP(X_i \in A)$$
Unione --> 3o assioma quindi sommatoria SE c è disgiunzione
Intersezione --> produttoria SE c è indipendenza

Funzione $g(X, Y) = Z$ con $Z$ variabile aleatoria SE il suo codominio è $R$
$$E(Z) = E(g(X, Y)) = \sum_{x \in D_x}\sum_{y \in D_y}g(x,y)*f_{X,Y}(x,y)$$
$$E(\sum_{i=1}^nX_i)=\sum_{i=1}^nE(X_i)$$
es
g(X,Y)=X+Y
E(g(X,Y)) = E(X)+E(Y)
`DIM` 
$=\sum_{x\in D_X}\sum_{y \in D_Y} (x+y)*f_{X,Y}(x,y)$
$=\sum_{x\in D_X}\sum_{y \in D_Y} x*f_{X,Y}(x,y)+\sum_{x\in D_X}\sum_{y \in D_Y} y*f_{X,Y}(x,y)$
$=\sum_{x\in D_X}x*\sum_{y \in D_Y} f_{X,Y}(x,y)+\sum_{y \in D_Y} y*\sum_{x\in D_X}f_{X,Y}(x,y)$
$=\sum_{x\in D_X}x*f_X(x)+\sum_{y \in D_Y} y*f_Y(y)$
$= E(X)+E(Y)$
Generalizzando ho dimostrato 
$$E(\sum_{i=1}^n X_i)=\sum_{i=1}^n E(X_i)$$

SE il valore atteso di una variabile aleatoria è difficile da calcolare, posso dividere tale valore atteso nella somma del valore atteso di piu variabili aleatorie

OSS voglio rimuovere aleatorietà da una variabile aleatoria, sostituendola con una costante: scelgo un valore $c$ per la variabile aleatoria $X$ conoscendo il suo valore atteso $E(X)=\mu$. 
Per capire se c è meglio serve una metrica
$E((X - c)^2)$ se $X$ fosse fissato sarebbe la distanza tra $X$ e $c$, mi darebbe l errore che avrei approssimando $X$ con $c$

$E(((X-\mu)+(\mu-c))^2)$
$= E((X-\mu)^2+ 2(X-\mu)*(\mu-c)^2+(\mu-c)^2)$
$= E((X-\mu)^2) + 2E(X-\mu)*(\mu-c)^2+(\mu-c)^2)$
$E(X-\mu)=0$ perchè $E(X)-E(\mu)=\mu-\mu=0$
$E((X-\mu)^2) + (\mu-c)^2>0$

Ho dimostrato che $E((X - c)^2) \geq E((X -\mu )^2) = \sigma^2$
Quindi $\mu$ mi permette di ottenere il piu piccolo errore