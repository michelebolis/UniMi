Consideriamo un insieme di valori osservati $X= \{x_1, .., x_n\}$ con le rispettive frequenze relative $f_1, …, f_n$
Consideriamo una trasformazione $g$ che trasforma i valori di $X$ in valori appartenenti all'insieme $Y=\{x'_1, …, x'_n\}$
$\forall i = 1, …, n, g(x_i) = x'_i$

Trasformazioni lineari
Fissate due costanti $a, b\in R$, il valore originale $x$ verrà trasformato in un valore $x'$ secondo la regola
$x'=g(x) = a*x + b$

- Traslazione

Traslazione per una costante $k>0$,
- Traslazione a sinistra: $x -> x' = x - k$
- Traslazione a destra: $x -> x' = x + k$

Scelte di $k$
- Minimo degli $v_i$, il più piccolo $v'_i$ vale 0
- Media campionaria, …

Osservazioni sugli indici:
- Media campionaria: è la stessa media campionaria originale applicando la stessa traslazione
- Mediana campionaria: è la stessa mediana campionaria originala applicando la stessa traslazione
- Varianza campionaria: rimane la stessa
- Deviazione standard: rimane la stessa
- Range interquartile: rimane uguale (ottenendosi da 3o quartile - 1quartile si traslano entrambi e quindi con la differenza rimane uguale)
- Range rimane uguale
- La media, la mediana e i quantili vengono traslati della stessa quantità $k$
- Il range, la distanza interquartile, la varianza e la deviazione standard rimangono gli stessi dell'insieme $X$

![[Pasted image 20240409103321.png]]

- Cambiamento di scala / scalatura: dilatazione o contrazione

Dilatare i valori di un fattore costante $h\in R^+$, applichiamo la trasformazione $x -> x' = \frac{x}{h}$ 
SE $h > 1$ il range dei valori risulta diminuito
SE $h < 1$ il range dei valori risulta dilatato
SE $h < min$, allora tutti i valori trasformati saranno maggiori di 1
SE $h > max$, allora tutti i valori trasformati saranno minori di 1

- La media, la mediana e i quantili vengono scalati della stessa quantità 
- Il range di variazione e la distanza interquartile vengono scalati della stessa quantità 
- La varianza viene scalata di una quantità  mentre la deviazione standard di 

- Cambiamento di origine e scala

SE abbiamo un insieme di valori nell'intervallo $(a, b)$ e vogliamo adattarli in modo che appartengano all'intervallo $(c, d)$

la trasformazione da applicare sarà $x -> x' = c + \frac{d-c}{b-a}*(x - a)$
- SE vogliamo trasporre in $[0, 1]: x -> x' = \frac{x-a}{b-a}$ 
- SE $a=0$, la trasformazione precedente consiste nel dividere i dati per il valore massimo $b$
- SE vogliamo trasporre in $[-1, 1]: x -> x' = 2 * \frac{x-1}{b-1}- 1$

- Standardizzazione

Consiste nell'applicare una scala il cui fattore è uguale alla deviazione standard dei valori per poi traslare verso sinistra rispetto alla media dei valori
SE $\overline x$ è la media campionaria e con $\sigma_x$ la deviazione standard campionaria
$x -> x' = \frac{x-\overline x}{\sigma_x}$
La trasformazione di standardizzazione trasforma l'insieme dei valori in un altro insieme di valori la cui media è 0 e la varianza è 1

es
```python
transformed_strength = (strength - strength.mean()) / strength.std()
```

In realtà la media non sarà esattamente 0 in quanto le operazioni sono fatte in virgola mobile e richiedono approssimazioni

- Trasformazioni logaritmiche

Utile quando ho valori molto grandi o molto distanti infatti il logaritmo mi linearizza dati di diverse scale di grandezza
$x -> x' = \log x$
La scelta della base del logaritmo viene di norma fatta a seconda della situazione da affrontare (tipicamente 10, costante di Napier e circa 1.72 o 2)

Nel caso in cui i valori siano molto distanziati e abbiano una distribuzione di frequenza unimodale fortemente asimmetrica, la trasformazione logaritmica permette di ottenere una distribuzione piu simmetrica

