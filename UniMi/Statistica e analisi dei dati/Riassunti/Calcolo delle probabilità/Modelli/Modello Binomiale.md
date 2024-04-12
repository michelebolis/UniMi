Il modello binomiale è descritto da una variabile aleatoria $X$ che denota il numero di successi della ripetizioni per n volte in modo indipendente di un esperimento Bernoulliano di parametro $p$
$$X \sim B(n, p)$$
$X =$ numero di successi
$n\in N,p\in[0, 1]$
$D_X = \{0, …, n\}$

Dato $i\in D_X$
$p^i * (1 - p)^{(n - i)} = p*…*p$//i volte $* (1 - p) * … *(1 - p)$ //$n - i$ volte

$$f_X(i)=P(X = i)=\binom{n}{i}*p^i*(1 - p)^{(n - i)}*I_{\{0, …, n\}}(i)$$
OSS $\sum_{i=0}^nf_X(i)=\sum_{i=0}^n\binom{n}{i}*p^i*(1-p)^{(n - i)}=(p-p+q)^n=1^n$
Sapendo che $(a+b)^n=\sum_{i=0}^n\binom{n}{i}*a_i*b^{(n - i)}$

Grafichiamo distribuzione binomiale
$X\sim B(n, p), D_X =\{0, …, N\}$
$$f_X(x) =\binom{n}{x}*p^x*(1-p)^{ n-x}$$
Voglio sapere quando la funzione è crescente: $f_X(x + 1) >= f(x)$ VERO fino a una certa $x$ in cui o ho due barre uguali () e poi ho una decrescita oppure ho una barra centrale e poi la decrescita
Ottengo un grafico a bastoncini approssimativamente simmetrico

$$E(X) = np$$
$np$ sarà compreso tra i due bastoncini uguali centrali
es $f_X$
![[Pasted image 20240411100038.png]]

DIM $E(X) = np$
$E(X) = \sum_{x=0}^n x*\binom{n}{x}*p^x*(1-p)^{n-x}$
Introduco $n$ variabili aleatorie $i=1, …, n$
$X_i = \begin{cases} 1 \text{ SE ho successo all'i-esima prova} \\ 0 \text{ SE non ho successo all'i-esima prova} \end{cases}$
$X = \sum_{i=1}^n X_i$
$E(X) = E(\sum_{i=1}^n X_i)$
$E(X) = \sum_{i=1}^n E(X_i)$
Dato che $X_i$ segue il modello bernoulliano
$E(X) = \sum_{i=1}^n p$
$E(X) = n * p$

OSS SE $p$ è elevato, $np$ si sposta verso $n$, è ragionevole perche sarà piu facile che l'esperimento abbia successo e quindi avro piu probabilmente un numero piu elevato di successi

$$Var(X) = np*(1 - p)$$
DIM
$Var(X) = Var(\sum_{i=1}^n X_i)$
$Var(X) = \sum_{i=1}^n Var(X_i)$ //ATT posso perche sono indipendenti 
$Var(X) = \sum_{i=1}^n p*(1-p)$
$Var(X) = n * p * (1-p)$
Avro un arco di parabola da 0 a 1 con max in $p = \frac{1}{2}$

Proprietà:
SE $X_1$ e $X_2$ seguono una legge binomiale, $X_1\sim B(n_1, p)$ e $X_2\sim B(n_2, p)$
$X_1 = \sum_{i=1}^{n_1} X_{1i}$
$X_2 = \sum_{i=1}^{n_2} X_{2i}$
$X_1 + X_2 = \sum_{i=1}^{n_1} X_{1i} + \sum_{i=1}^{n_2} X_{2i}$

Nonostante siano due variabili diverse, seguono la stessa distribuzione
$Y_i= X_{1i}$ con $i=1, …, n_1$
…
$X_1+X_2 = \sum_{i=1}^{n_1+n_2}X_i$
$$X_1+X_2 \sim B(n_1+n_2, p)$$
