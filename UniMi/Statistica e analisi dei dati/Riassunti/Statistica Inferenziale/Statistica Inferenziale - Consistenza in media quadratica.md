Provo a calcolare la $Var(X)$ con $t(X_1, …, X_n)=\overline x=\frac{1}{n} * \sum_{i=1}^n X_i$
$$Var(\frac{1}{n}*\sum_{i=1}^n X_i)=\frac{1}{n^2}*\sum_{i=1}^n Var(X_i)=\frac{1}{n^2}*\sum_{i=1}^n Var(X)=\frac{Var(X)}{n}$$
//dato che $X_i$ ha la stessa distribuzione della popolazione $X$ hanno la stessa $Var$ e $E$

Varianza dello stimatore: quanto vicino sono le stime, quanto piu basso è tale valore meglio è, MA dipende da $X$ e da $n$ PERO ho $n$ al denominatore, scegliendo $n$ grande, possiamo far diventare questo valore piccolo a piacere

Introduciamo
$$MSE_{\tau(\Theta)}(t(X_1,...,X_n))=E((t(X_1,...,X_n)-\tau(\Theta))^2)$$
MSE = Mean Square Error indica la discrepanza media tra i valori assunti osservati e la quantità da stimare

Abbiamo sempre pensato $n$ come fisso
Consistenza in media quadratica: cattura SE all'aumentare della numerosità del campione, il suo MSE si concentra sulla quantità di interesse
SE $\forall \Theta \lim_{n->\infty}MSE_{\tau(\Theta)}(t(X_1,...,X_n))$ 
ALLORA lo stimatore è consistente in media quadratica

Uno stimatore non è necessariamente non deviato MA
SE non deviato, $$MSE(T) = Var(T)$$
`DIM`
SE è non deviato, ALLORA $E(t(X_1,…,X_n))=\tau(\Theta),MSE_{E(t(X_1,…,X_n))}=E((t(X_1,…,X_n))- E(t(X_1, …, X_n))^2)$
SE per brevità $t(X_1, …, X_n)=T_n,MSE_{T_n}= E(T - E(T)^2) = Var(t(X_1, …, X_n))$

SE uno stimatore è distorto, vale la pena calcolare la consistenza in media quadratica? Magari un campione su n elementi è distorto, ma asintoticamente potrebbe essere non deviato

QUINDI prima $MSE_{\tau(\Theta)}(T) =Var(T)-b_{\tau(\Theta)}(T)^2$  dimostrando che  è non deviato e gode della proprieta di consistenza in media quadratica

$$MSE_{\tau(\Theta)}(T) =Var(T)-b_{\tau(\Theta)}(T)^2$$
`DIM`  
$MSE_{\tau(\Theta)}(T)=E(T-\tau(\Theta))^2$
$= E(T-E(T)+E(T)-\tau(\Theta))^2$
$=E(T-E(T))^2+2*E((T-E(T)*(+E(T)-\tau(\Theta)))+E(E(T)-\tau(\Theta))^2$
$=E(T-E(T))^2+E(E(T)-\tau(\Theta)))^2$

Coerente perche SE stimatore non deviato $MSE(T) = Var(T)$ perche $b$ è nullo


La proprieta di consistenza si puo definire in un altro modo
Popolazione $X \sim F(\Theta), \tau(\Theta)$ quantita da stimare dato un campione $X_1, …, X_n$
Consideriamo una successione $T_1, …, T_n$ di variabili aleatorie che corrispondono alla quantita restituita da uno stimatore sugli $n$ elementi del campione

Variabile aleatoria $|T_n - \tau(\Theta)|$
Evento $|T_n - \tau(\Theta)|< \varepsilon$
$P(|T_n - \tau(\Theta)|< \varepsilon)$ si verifica quando l'errore, stimando $\tau(\Theta)$ con lo stimatore $T_n$, è minore di $\varepsilon$
Voglio questa P grande

$$\text{SE } \varepsilon>0 \wedge\lim_{n->\infty}P(|T_n - \tau(\Theta)|< \varepsilon)=1$$
ALLORA il mio stimatore è debolmente consistente
SE consistente in media quadratica ALLORA è anche debolmente consistente MA NON è garantito il viceversa
DIM
$P(|T_n - \tau(\Theta)|< \varepsilon) = P((T_n - \tau(\Theta))^2< \varepsilon^2) = 1-P(P((T_n - \tau(\Theta))^2> \varepsilon^2))$
Ricordandoci la disuguaglianza di Markov
$\geq 1-\frac{(T_n - \tau(\Theta))^2}{\varepsilon^2} = 1-\frac{MSE_{\tau(\Theta)}(T_n)}{\varepsilon^2}$
SE $T_n$ è consistente in media quadratica per $\tau(\Theta)$, $\lim_{n->\infty} 1-\frac{MSE_{\tau(\Theta)}(T_n)}{\varepsilon^2}=1$ QUINDI è anche debolmente consistente 