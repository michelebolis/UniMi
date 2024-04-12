Dato un campione ${a_1, …, a_n}$ in cui occorrono i valori distinti $v_1, …, v_s$ e indicando con $f_i$ la frequenza relativa dell'elemento $v_i$ per $i= 1, …, s$
$$H = \sum_{i=1}^sf_i*\log\frac{1}{f_i}=-\sum_{i=1}^sf_i*\log f_i$$
OSS Fissando un addendo, un $i$, frequenza relativa * log del suo inverso

La funzione $p -> \log \frac{1}{p}$ è detta autoinformazione ed il suo andamento in (0, 1] è il seguente
![[Pasted image 20240409094939.png]]

Scelta della base del logaritmo cambia l'unita di misura con cui misuro l entropia, $\log_2$ si dice che l'entropia è espressa in bit

Estendendo la definizione del generico addendo anche per fi=0, ponendolo uguale a 1

$$\forall i, - f_i * log f_i \geq 0 \implies H \geq 0$$$$\forall i, - f_i * \log f_i = 0 \Leftrightarrow f_i = 0 \vee f_i = 1$$
Quindi $H = 0$ SE E SOLO SE ci si trova in una condizione di massima omogeneità

$$H = 0 \Leftrightarrow \exists j | f_j = 1 \wedge \forall i \neq j, f_i = 0$$

Massima eterogeneità quando $f_i = \frac{1}{s}$ e quindi $H = \log s$
 
Consideriamo l'indice di entropia normalizzato $H'$ che assume valori tra 0 e 1
$$H' = \frac{H}{\log s}$$
```python
def entropy(series):
    return sum((series.value_counts(normalize=True).map(lambda f: -f * np.log2(f))))
def entropy(series, normalized=False):
    freq = series.value_counts(normalize=True)
    e = sum((freq.map(lambda f: -f * np.log2(f))))
    if normalized: e /= np.log2(len(freq))
    return e
```