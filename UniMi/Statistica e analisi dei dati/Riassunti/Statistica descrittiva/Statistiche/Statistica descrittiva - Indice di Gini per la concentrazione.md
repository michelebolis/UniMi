I valori assunti dagli individui sono rappresentanti di una certa "ricchezza"
Analizziamo come la ricchezza della popolazione è distribuita nel campione

Date $n$ osservazioni, $a_1, …, a_n$ elenco ordinato di tale osservazioni
Calcoliamone il valore medio $\overline a=\frac{1}{n}*\sum_{i=1}^n a_i$ 
$TOT= n * \overline a=\sum_{i=1}^n a_i$
- Concentrazione minima / equo: tutti gli elementi assumono lo stesso valore 
- Concentrazione massima / sperequato: tutti gli elementi assumono valore 0 a parte uno che assume valore $n * \overline a$

Consideriamo fissando $i$ (sto dividendo il mio campione)
- Frequenza relativa cumulata fino all'i-esima osservazione $F_i = \frac{i}{n}$ per $i= 1, …, n$
- Quantità relativa cumulata fino all'i-esima osservazione: $Q_i = \sum_{k=1}^n \frac{a_k}{TOT}$

Proprietà
- $0 \leq F_i \leq 1$ 
- $0 \leq Q_i \leq 1$
- $Q_i \leq F_i$ dato che le osservazioni sono ordinate in modo crescente
- $Q_i = F_i$ nella concentrazione minima
- $Q_n = F_n$

Uso un piano cartesiano con $F_i$ sulle $x$ e $Q_i$ sulle $y$
- Concentrazione minima:

Tutti gli $n$ punti $(F_i, Q_i)$ giacciono sulla retta $F = Q$ bisettrice del primo e del terzo quadrante
es
```python
tot = 10
n = 20
a = [tot/n] * n
q = np.cumsum(a) / tot
f = np.arange(1, n+1) / n
plt.plot([0, 1], [0, 1], linestyle='--', linewidth=2, c='gray')
plt.plot(f, q, 'o')
plt.show()
```
![[Pasted image 20240409101349.png]]

- Concentrazione massima:

I punti per $i= 1, …, n-1$ giacciono sulla retta $Q = 0$ mentre l'ultimo ha $F_n = Q_n = 1$
es
```python
tot = 10
n = 20
a = [0] * (n-1) + [tot]
q = np.cumsum(a) / tot
f = np.arange(1, n+1) / n
plt.plot([0, 1], [0, 1], linestyle='--', linewidth=2, c='gray')
plt.plot(f, q, 'o')
plt.show()
```
![[Pasted image 20240409101439.png]]

- Caso generale

Nei casi generali si avrà che i punti staranno su una curva sotto la retta $F=Q$
Unendo i punti arrivo sempre a $(1, 1)$. Piu sono vicino all'asse delle x, più sono vicino al caso sperequato mentre più sono vicino alla bisettrice più sono vicino al caso equo.
La spezzata ottenuta è la curva di Lorenz.
L'area tra la curva di Lorenz e la bisettrice si chiama area di concentrazione (caso equo=0 mentre caso sperequato=?)

Definiamo l'indice di concentrazione / coefficiente / indice di Gini per la concentrazione
$$G = \frac{\sum_{i=1}^{n-1}F_i-Q_i}{\sum_{i=1}^{n-1}F_i}$$

OSS inutile somma fino a $n$ perché so che è 0
Non è esattamente l'area di concentrazione
- $Q_i - F_i$ è il segmento che collega la bisettrice alla spezzata
- $F_i$ al denominatore è un upper bound per normalizzare l'indice di Gini (normalizzare ci permette di avere come massimo valore dell'indice 1)

$0 \leq G \leq 1$
- SE $G=1$ caso sperequato
- SE $G=0$ caso equo

$$\sum_{i=1}^{n-1}F_i = \frac{1}{n}\sum_{i=1}^{n-1}i = \frac{1}{n}\frac{n(n-1)}{2}=\frac{n-1}{2}$$
$$G = \frac{2}{n-1}\sum_{i=1}^{n-1}F_i-Q_i$$
