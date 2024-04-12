- Media campionaria
La media ci indica attorno a quale valori si collocano i valori del campione
La media valuta la centralità dei dati, il baricentro, $\overline{x}$
$$\overline{x} = \frac{\sum_{i=1}^nx_i}{n}$$

Supponiamo di disporre di una tabella delle frequenze che elenca k valori distinti $x_1, …, x_k$ con le rispettive frequenze $f_1, …, f_k$. Il numero di osservazioni sarà dato dalla $\sum_{i=1}^kf_i$.
La media campionaria per ogni insieme di dati è:
$$\overline{x} = \frac{\sum_{i=1}^kf_i*x_i}{n}$$

In Series ho un metodo per calcolare la media
Proprietà: avendo i dati di un campione posso trasformarli, per esempio traslandoli di un c; la media campionaria del nuovo campione sarà la stessa la traslazione della media campionaria originale
Stessa proprietà vale per la scalatura (prodotto)
Utile per valori elevati
Trasformazione lineare dei dati non cambia la media, l'operatore media (n-ario) è lineare

MA la media non è robusta rispetto ai valori fuori scala o outliner
Svantaggi della media: è molto influenzata da valori estremi

- Mediana campionaria
Un altro indice per calcolare la centralità dei dati è la mediana campionaria
La mediana è un valore $\geq$ di almeno la metà dei dati e un valore $\leq$ di almeno la metà dei dati.
Se numero pari di osservazioni, la mediana campionaria è la media dei valori intermedi
$$m = \begin{cases} \frac{n+1}{2} \text{esimo valore SE n è dispari} \\ \frac{n}{2} \text{esimo valore SE n è pari} \end{cases}$$

La mediana è robusta rispetto agli outliner tuttavia considera solo uno o due valori centrali.

- Moda campionaria
La moda campionaria è l'osservazione con la maggior frequenza
SE non esiste un unico valore, allora tutti i valori sono detti valori modali

Non posso sempre calcolare tutti e 3 gli indici
La mediana è calcolabile solo se esiste un ordine per le osservazioni
La media richiede che le osservazioni siano numeriche

Gli attributi possono essere
- Scalari/numerici/quantitativi: posso usare media, mediana e moda
- Categorici/qualitativi: possono essere numerici o no
	- Ordinali: mediana e moda
	- Non ordinali: solo moda

//Gli attributi numeri ereditano le proprieta e le operazioni dei numeri. MA non sempre i numerici sono scalari
