Osservazioni di un medesimo attributo divise in $G$ gruppi, con $n_1, …, n_G$ le numerosità dei vari gruppi con $n = n_1 + … + n_G$ il numero totale di osservazioni e fissato $g \in \{1, …, G\}$ e $i \in \{1, …, n_G\}$ con $x_i^g$ il valore dell'i-esima osservazione del gruppo $g$

SE si è interessati a valutare l'ipotesi che i valori delle medie nei vari gruppi siano sensibilmente differenti, è possibile applicare il metodo ANOVA, ANalysis Of VAriance
Ipotesi: non ci siano differenze sostanziali tra i gruppi, calcolo quindi la varianza di un gruppi qualsiasi

- Media campionaria su tutte le osservazioni
$$\overline x = \frac{1}{n} \sum_{g=1}^G\sum_{i=1}^{n_g}x_i^g$$
- Media campionaria all'interno del g-esimo gruppo, $\forall g=1,...,n_g$
$$\overline{x_g} = \frac{1}{n_g}\sum_{i=1}^{n_g}x^g_i$$
- $SS_T$ somma totale degli scarti
$$SS_T=\sum_{g=1}^G\sum_{i=1}^{n_g}(x_i^g-\overline x)^2$$
- $SS_W$ somma degli scarti entro/within i gruppi
$$SS_W=\sum_{g=1}^G\sum_{i=1}^{n_g}(x_i^g-\overline x^g)^2$$
- $SS_B$ somma degli scarti tra/between i gruppi
$$SS_B=\sum_{g=1}^G n_g*(\overline x^g-\overline x)^2$$
Si puo dimostrare che 
$$SS_T=SS_W+SS_B$$
Quindi
Varianza totale = $\frac{n-G}{n-1} *$ varianza entro i gruppi + $\frac{n-G}{n-1} *$ varianza tra i gruppi

SE la varianza totale e la varianza entro i gruppi assumono valori non troppo diversi si confuta l'ipotesi che le medie new gruppi siano diverse

Se non ci sono significative differenze, calcolando la media campionaria di un singolo gruppo dovrò essere simile a quella totale, quindi la varianze dei singoli gruppi dovrebbe essere simile mentre quella totale 0

Entrambi gli addendi hanno un apporto sostanziale oppure il secondo è quasi zero e quindi la varianza tra i gruppi è quasi uguale quindi ho la media dei vari gruppi simile

Funzione che accetta una lista di gruppi e restituisce una coppia i cui elementi saranno la varianza totale e la varianza tra i gruppi

```python
import numpy as np
def anova(groups):
    all_elements = pd.concat(groups)
    sum_total = sum((all_elements - all_elements.mean())**2)
    sum_within = sum([sum((g - g.mean())**2) for g in groups])
    sum_between = sum([len(g) * (g.mean()-all_elements.mean())**2 for g in groups])
    assert(np.abs(sum_total - sum_within - sum_between) < 10**-5)
    n = len(all_elements)
    total_var = sum_total / (n-1)
    within_var = sum_within / (n-len(groups))
    return (total_var, within_var*(n-len(groups))/(n-1))
```

