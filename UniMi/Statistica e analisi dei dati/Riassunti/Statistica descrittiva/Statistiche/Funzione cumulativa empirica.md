SE i valori osservati sono numeri o ordinali, possiamo utilizzare la funzione cumulativa empirica / funzione di ripartizione empirica che dato un insieme di osservazioni $(x_1, …, x_n)$ è definita come $\hat{F}: R --> [0, 1]$ t.c. $\forall x\in R$ assume un valore pari alla frequenza relativa delle osservazioni che risultano essere <= x

$$\hat{F}= \frac{\#[x_i\leq x]}{n} = \frac{1}{n}*\sum_{i=1}^{n}I_{-\infty, x}(x_i)$$

Con:
- \# operatore di cardinalità
- $I_A: R --> [0, 1]$ è la funzione indicatrice dell'insieme A che assume valore nullo in corrispondenza di tutti i valori non appartenenti ad A e valore unitario altrimenti

E' possibile calcolarla utilizzando il modulo statmodels.api in particolare la funzione distributions.ECDF che riceve in input un'insieme di osservazioni

Il grafico di tale funzione sarà costante a tratti, rappresentabile con plt.step specificando l'asse delle x e delle y (ottenibile facendo ecdf(x) con ecdf la variabile che contiene la funzione)
OSS Tale grafico diventa indistinguibile da quello plt.plot all'aumentare dei casi osservati

```python
import statsmodels.api as sm
ecdf = sm.distributions.ECDF(heroes_with_year['First appearance'])
min_year = min(heroes_with_year['First appearance'])
max_year = max(heroes_with_year['First appearance'])
x = np.arange(min_year, max_year+1)
y = ecdf(x)
plt.step(x, y)
plt.show()
```

es
![[Pasted image 20240401190032.png]]