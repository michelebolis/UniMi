La legge debole dei grandi numeri afferma che la media aritmetica di $n$ copie indipendenti di una variabile aleatoria tende al valore atteso di quest'ultima per n che tende all'infinito

Sia $X_1, X_2, …$ una successione di variabili aleatorie indipendenti e identicamente distribuite, tutte con media $E(X_i) = \mu$, allora $\varepsilon >0,P(|\frac{X_1+...+X_n}{n} - \mu| > \varepsilon) -> 0$ per $n -> +\infty$

Applicazione di questo teorema: supponiamo di ripetere in successione molte copie indipendenti di un esperimento in ciascuna delle quali puo verificarsi un certo evento $E$
$X_i = \begin{cases} 1 \text{ SE E si realizza nell'esperimento i-esimo} \\ 0\text{ SE E non si realizza nell'esperimento i-esimo} \end{cases}$

La sommatoria $X_1 + … + X_n$ rappresenta il numero di prove in cui si è verificato $E$ e poiché $E(X_i) = P(X_i = 1) = P(E)$, si deduce che la frazione delle $n$ prove nelle quali si realizza $E$ tende alla probabilità $P(E)$