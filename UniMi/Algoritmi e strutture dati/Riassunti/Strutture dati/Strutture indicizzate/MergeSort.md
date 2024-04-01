Array di $n$ elementi $A[0…N-1]$
Caso migliore: 1 elemento nell'array
E' più facile ordinare array piccoli --> divido il problema in due parti, le ordino e poi le fondo

SE $n\leq1$, $A$ è ordinato
ALTRIMENTI
- Dividi $A$ in due parti circa della stessa lunghezza
- Ordina le due parti separatamente
- Fondi i due array ordinati in un unico array: [[Array - Merge]]

```
ALGORITMO mergeSort(array A[0…N-1])
IF n>1 THEN
	m <- n/2
	B <- A[0…m-1] //prima meta di A
	C <- A[m…N-1] //seconda meta di A
	mergeSort(B)
	mergeSort(C)
	A <- merge(B, C)
//ci sarebbe else non fare niente
```

[[Divide et impera]]
Numero Confronti Per Ordinare Array Di N Elementi = 
$$C(n) =\begin{cases} 0 \text{ SE } n=1 \\ C(\lfloor \frac{n}{2} \rfloor)+C(\lfloor \frac{n}{2} \rfloor)+C_{merge}(n) \text{ SE } n>1 \end{cases}$$
Sapendo che
$$\sum_{i=0}^{k-1}{2^i} = 2^k -1$$
Dato $n$ trovare $N$ potenza di 2 t.c $n\leq N$ con $N$ il piu piccolo possibile
Per ogni $n$ esiste una potenza di 2, $N$, t.c. $n<=N<2*n$

Considerando che $C_{merge}= n-1$
- SE $n$ pari:
$$C(n)= \begin{cases} 0 \text{ SE } n=1
\\2*C(\frac{n}{2}) + n-1 \text{ SE } n>1 \end{cases}$$

$$C(n)= 2*C(\frac{n}{2}) + n-1 = 2 (2* C(\frac{n}{2^2}) + \frac{n}{2} -1) + n-1 = 2^2 * C(\frac{n}{2^3}) + n-2 + n-1$$
$$= 2^2 * [2*C(\frac{n}{2^3}) + \frac{n}{2^2} -1 ] + n-2 + n-1 = 2^3 * C(\frac{n}{2^3}) + n-2^2 + n-2^1 + n-2^0$$
$$= 2^k * C(\frac{n}{2^k}) + k*n - \sum_{i=0}^{k-1}{2^i} = 2k * C(\frac{n}{2^k}) + k*n - 2^k +1$$

Per quale valore di $k$, $\frac{n}{2^k}=1$? $n=2^k$ quindi $k=\log_2 n$
$C(n) = n * C(1) + n \log_2 n -n +1 = n \log_2 n -n +1$ // per $n$ potenza di 2
$C(n) = \Theta(n*\log n)$

In generale: esiste $N$ potenza di 2 con $n<=N<2*n$
$$C(n) \leq C(N) = N*\log_2 N -N +1 < 2n * \log_2 2n -n +1 $$$$= 2n ( 1+ \log_2 n) -n+1 = 2n + 2n \log_2 n -n +1 = 1 $$$$2n*\log_2 n + n +1 = Θ(n \log n)$$

Tempo T(n):
- Devo copiare elementi dell'array A in un nuovo array --> $\Theta(n)$
- Chiamate ricorsive: $T(\lfloor \frac{n}{2} \rfloor) + T(\lfloor \frac{n}{2} \rfloor)$
- Tempo merge + tempo copiare il risultato in $A = \Theta(n) + \Theta(n)$ //se confronti $Ο(1)$

$T(n)= \Theta(n)+ T(\lfloor \frac{n}{2} \rfloor) + T(\lfloor \frac{n}{2} \rfloor) + \Theta(n) = T(\lfloor \frac{n}{2} \rfloor) + T(\lfloor \frac{n}{2} \rfloor) + bn+c$
SE $n=1$, $T(1) = 1$

$T(n)= 2*T(\lfloor \frac{n}{2} \rfloor) + bn+c$
$a$ ALTRIMENTI

$T(n)= bn \log_2 n + a*n + c*(n-1) = \Theta(n*\log n)$

Spazio: disastroso
$H(n)$ = altezza dello stack ricorsione su array $n$

Altezza massima: chiamata in esecuzione + chiamate in attesa
SE $n>1$, $H(n)= 1+ max(H(\lfloor \frac{n}{2} \rfloor), H(\lfloor \frac{n}{2} \rfloor))$ //massimo perché uso stesso spazio

$$H(n)= \begin{cases} 1+ max(H(\lfloor \frac{n}{2} \rfloor), H(\lfloor \frac{n}{2} \rfloor)) \text{ SE } n>1 \\ 1 \text{ ALTRIMENTI} \end{cases}$$

Per n pari:
$H(n) = \begin{cases} 1+H(\frac{n}{2})\\ 1 \end{cases}$

$H(n) = 1+ \log_2 n$ //per $n$ potenza di 2
In generale $H(n)= 2 + \log_2 n = \Theta(\log n)$

In questa soluzione ho sia uno spreco di spazio, utilizzando gli array $B$ e $C$, sia uno spreco di tempo, copiando il contenuto di A

Soluzione: unico array ausiliare $X$ per il merge
[[Array - Marge migliorato]]

```
PROCEDURA mergeSort(Array A, indice i, indice f, Array X) 
//per una generica porzione di A
IF f-i >1 THEN
	m <- (i+f)/2
	mergeSort(A, i, m, X)
	mergeSort(A, m, f, X)
	merge(A, i, m, f, X)

ALGORITMO mergeSort(Array A[0…N-1])
// Sia X un array di lunghezza n
mergeSort(A, 0, N, X)
```

Spazio: 
- STACK $altezza*spazioCostante = \Theta(\log n)$
- Array ausiliario $X = \Theta(n)$
Spazio = $\Theta(n)$

Numero Confronti (sempre nel merge) $= \Theta(n*\log n)$
$Tempo= \Theta(n*\log n)$ // SE confronti $Ο(1)$
