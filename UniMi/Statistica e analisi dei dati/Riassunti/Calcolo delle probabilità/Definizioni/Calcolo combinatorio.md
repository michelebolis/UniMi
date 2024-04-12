Serve per studiare in quanti modi diversi si possono fare raggruppamenti
Fattori da considerare:
- Nei raggruppamenti in cui faccio conta l'ordine?
- Posso ripetere gli oggetti?

Principio fondamentale del calcolo combinatorio: SE ci sono $s_1$ modi per operare una scelta e, per ciascuno di essi, ci sono $s_2$ modi per operare una seconda scelta e cosi via fino a st modi per operare la t-esima scelta, ALLORA il numero di sequenze di possibili scelte è $s_1 * s_2 * … * s_t$

OSS corrisponde al numero delle foglie di un albero di profondità $t$
- Permutazioni

Consideriamo un insieme di $n$ oggetti $A = \{a_1, …, a_n\}$
La permutazione degli $n$ oggetti è una sequenza ordinata in cui compaiono tutti gli oggetti

- Permutazioni semplici (senza ripetizioni)

SE gli $n$ oggetti di $A$ sono tutti indistinguibili
Applichiamo il principio fondamentale del calcolo combinatorio
- I modi in cui selezionare l'oggetto in prima posizioni sono n
- Nella seconda posizione avremo $n-1$ oggetti quindi $n-1$ possibilità
- Facendo lo stesso per le altre posizioni alla posizione i-esima avremo $n-(i-1)$ elementi di $A$ tra cui scegliere
- QUINDI abbiamo costruito un albero di profondità $n$ che ha un numero di foglie pari a $$n * (n-1) * … * 1 = n!$$

- Permutazioni di oggetti distinguibili a gruppi

SE gli $n$ oggetti di $A$ sono distinguibili a gruppi di numerosità $n_1, n_2, …, n_k$ con $\sum_{i=1}^k n_i=n$
Chiamiamo $P_{n:n_1,...,n_k}$ il numero di configurazioni differenti 
$n! = P_{n:n_1,...,n_k}*n_1!*…*n_k!$
Quindi otteniamo il coefficiente multinomiale
$$P_{n:n_1,...,n_k} = \frac{n!}{n_1!*…*n_k!}=\binom{n}{n_1,...,n_k}$$ 

- Disposizioni

Consideriamo un insieme di n oggetti distinti $A=\{a_1, …, a_n\}$ e selezioniamo $k$ oggetti volendo distinguere le configurazioni contenenti gli stessi oggetti ma estratti in ordine differente
QUINDI è importante sia la posizione che l'oggetto

- Senza ripetizione / disposizioni semplici SE gli oggetti di $A$ possono essere usati una sola volta

$$d_{n, k} = \frac{n!}{(n-k)!}$$
è il numero di possibili disposizioni senza ripetizioni di n oggetti su k posti
OSS per $k=n$ le permutazioni semplici sono un caso particolare delle disposizioni semplici

- Con ripetizioni

$$D_{n, k} = n * n * … * n = n^k$$

- Combinazioni

Considerando $n$ oggetti presi $k$ alla volta ci interessa la sequenza di oggetti estratto

- Senza ripetizioni / combinazioni semplici

Dati $k$ oggetti, corrispondono $k!$ distinte disposizioni
Il numero totale di disposizioni semplici è uguale al numero di combinazioni moltiplicato per $k!$
$d_{n, k} = c_{n, k} * k!$
$$c_{n, k}=\frac{d_{n, k}}{k!}=\frac{n!}{(n-k)!*k!}=\binom{n}{k}$$
Coefficiente binomiale: quanti sottogruppi fatti da $k$ oggetti posso fare da $n$ 

- Con ripetizioni
$$C_{n, k} = \binom{n+k-1}{k}$$