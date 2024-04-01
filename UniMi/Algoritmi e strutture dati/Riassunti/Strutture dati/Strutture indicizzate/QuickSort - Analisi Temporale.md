Caso: array gia ordinato
Faccio $n$ confronti
In generale fa o $n$ o $n-1$ confronti

```
PROCEDURA quickSort(array A, indice i, indice f)
IF f-i >1 THEN
	m <- partizione(A, i, f)
	quickSort(A, i, m)
	quickSort(A, m+1, f)

ALGORITMO quickSort(array A[0…n-1])
quickSort(A, 0, n)
```

OSS Non ho introdotto strutture aggiuntive MA essendo ricorsiva uso lo stack. Noi lo consideriamo in loco

- Caso peggiore: tutti numeri gia ordinati, non si divide bene
$C(n)= n+ C(k)+C(n-k-1)$
$C(n)= \begin{cases} 0 \text{ SE } n\leq1 \\ n+max\{C_w(k)+C_w(n-k-1) | k=0…n-1\} \end{cases}$

$$C_w(n)= n+C_w(n-1) = n+n-1+C_w(n-2) = n+n-1+n-2+C_w(n-3)=…=$$ $$n+…+2+C(1) =\sum_{i=2}^{n}{i} = \frac{n(n+1)}{2} -1 = O(n^2)$$
- Caso migliore: il pivot si trova a meta, due parti di $\frac{n}{2}$ elementi
$C(n)= \begin{cases} 0 \text{ SE } n\leq1 \\ n+min\{C_b(k)+C_b(n-k-1) | k=0…n-1\} \end{cases}$
$C_b(n) \approx n + 2*C_b(\frac{n}{2})$
$C_b(n) \approx n*\log_2 n$

- Caso medio
$$C(n)=\begin{cases} 0 SE n\leq1 \\ \frac{\sum_{k=0}^{n-1}{n+C(k)+C(n-k-1)}}{n} \end{cases}$$
Supponendo una distribuzione uniforme, probabilità uniforme per ogni $k$
$$C(n)= \frac{1}{n} * \sum_{k=0}^{n-1}{n + \frac{1}n} * \sum_{k=0}^{n-1} C(n) + \frac{1}{n} * \sum_{k=0}^{n-1} C(n-k-1)$$
$$= n + \frac{1}{n} * (C(0)+…+C(n-1)) + \frac{1}{n} * (C(n-1)+…+C(0)) = n + \frac{2}{n} * (\sum_{i=0}^{n-1}{C(i)})$$
Sapendo che $C(0)=C(1)= 0$ da caso base 
$$n + \frac{2}{n} * \sum_{i=2}^{n-1}C(i)$$
$C(n)= \begin{cases} 0 \text{ SE } n\leq1 \\ n + \frac{2}{n} * \sum_{i=2}^{n-1}C(i) \end{cases}$

Dimostriamo che $C(n) \leq 2*n*\ln n$ per $n>=1$
Per induzione
- Base: $n=1$
$C(1)=0$ -> $2*1*\ln1 =0$ VERO
- Induzione: $C(n)= n+ \frac{2}{n} * \sum_{i=2}^{n-1}{C(i)}$ // uso ipotesi induttiva $2i \ln i$
$$C(n)= n+ \frac{2}{n} * \sum_{i=2}^{n-1}{C(i)} \leq n+ \frac{2}{n} * \sum_{i=2}^{n-1}{2*i \ln i} = n+\frac{4}{n} * \sum_{i=2}^{n-1}{i*ln i}$$
$$n+ \frac{2}{n} * \sum_{i=2}^{n-1}{C(i)} \leq n + \frac{4}{n} * (\frac{n^2}{2} * \ln n -\frac{n^2}{4} )$$
$$n+ \frac{2}{n} * \sum_{i=2}^{n-1}{C(i)} \leq n + 2n * \ln n - n$$
$$n+ \frac{2}{n} * \sum_{i=2}^{n-1}{C(i)} \leq + 2n * \ln n \approx 1,39 * n * \lg_2 n$$

QUINDI
Caso peggiore circa $n^2 / 2 = \Theta(n^2)$
Caso migliore circa $n*\log_2 n$
Caso medio circa $1,39*n*\log_2 n$

Caso medio e migliore sono ravvicinati, e dato che il caso medio contiene anche il caso peggiore ciò implica che il caso peggiore capiti poco spesso

OSS algoritmo molto sensibile alla scelta del perno (se il primo, quello nel mezzo…)
Una tecnica sarebbe quello di disordinare l array prima di riordinarlo per evitare di avere porzioni gia ordinate