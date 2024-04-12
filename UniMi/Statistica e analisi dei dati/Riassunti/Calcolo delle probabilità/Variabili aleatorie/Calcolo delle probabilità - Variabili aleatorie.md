ATT variabile in ambito del calcolo delle probabilità significa che ogni volta che la osservo è diversa, aleatoria cioè che cambia in modo casuale
Permette di codificare gli eventi in termini di numeri reali
Siccome il valore di una variabile aleatoria è determinato dall'esito dell'esperimento, possiamo assegnare delle probabilità ai suoi valori possibili

Data la terna $(\Omega, A, P)$ con $\Omega$ lo spazio campionario, $A$ l'algebra degli eventi e $P$ la funzione di probabilità
$X: \Omega --> R$ è una funzione che associa ad ogni esito un numero reale
NON tutte le funzioni cosi rappresentano una variabile aleatoria

SE X = somma degli esiti di un lancio di 2 dati (abuso di notazione per X)
SE {X = 3} significa che l esperimento eseguito ha dato come risultato 3
Posso calcolare $P({X= 3})=P({(1, 2) \cup (2, 1)}) = 2/36$
//si può evitare di mettere le graffe per X=…

Siccome il codominio di R per ogni valore reale che osservo devo poter calcolare la probabilità
Prendendo un generico $\alpha \in R, X^{-1} (\alpha) = \{w \in \Omega | X(w) \leq \alpha \}$ e siccome è un sottoinsieme di $\Omega$ voglio che $\alpha \in A$, SE questo è vero allora $X$ è una variabile aleatoria

Posso creare diverse variabili aleatorie per la stessa terna
Es Y=esito del primo lancio
$P(Y=i)= 1/6$

I valori che possono essere assunti da una variabile aleatoria si chiamano specificazioni
L'insieme delle specificazioni è il dominio / supporto (in questo caso i supporti sarebbero gli interi da 1 a 6)

Funzione indicatrice IA con A insieme, IA funzione a valori binari 1 o 0
$I_A(x) = \begin{cases} 1 \text{ SE } x \in A\\0 \text{ SE } x \notin A \end{cases}$
È come se fosse un filtro

Es $P(Y=i)= 1/6 * I_{\{1, …, 6\}}(i), \forall i \in R$
Notiamo che $A$ in questo caso è il supporto di $Y$

Le variabili aleatorie con un numero finito o numerabile di un valori possibili sono dette discrete. [[Calcolo delle probabilità - Variabili aleatorie discrete]]
Le variabili aleatorie che possono assumere un insieme continuo di valori possibili sono dette continue [[Calcolo delle probabilità - Variabili aleatorie continua]]

[[Valore atteso]]
[[Varianza]]
[[Variabili aleatorie congiunte]]
[[Covarianza]]