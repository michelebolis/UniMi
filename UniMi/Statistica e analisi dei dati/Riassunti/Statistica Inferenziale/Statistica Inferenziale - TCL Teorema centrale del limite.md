Popolazione X, campione $X_1, …, X_n$ con $\overline X=\frac{1}{n}*\sum_{i=1}^n X_i$

$E(X) = \mu$ e $Var(X) =\sigma^2$ ALLORA $\sum_{i=1}^n X_i \sim.N(n\mu,\sqrt n\sigma)$

Anche la $\frac{1}{n}*\sum_{i=1}^n X_i$ sarà approssimativamente normale
QUINDI media campionaria ha una distribuzione approssimativamente normale

Popolazione $X$ con $E(X) = \mu$ e $Var(X) = \sigma^2$, $\tau(\Theta) =\mu$ , consideriamo $X_1, …, X_n$ campione
$$P(|\overline X -\mu \leq r|)\geq 1-\delta$$
$$P(-r\leq \overline X -\mu \leq r) \geq 1-\delta$$
$$P(\frac{-r}{\sigma}\sqrt n\leq \frac{\overline X-\mu}{\frac{\sigma}{\sqrt n}} \leq \frac{r}{\sigma}\sqrt n) \geq 1-\delta$$
Approssimiamo
$$P(\frac{-r}{\sigma}\sqrt n\leq \frac{\overline X-\mu}{\frac{\sigma}{\sqrt n}} \leq \frac{r}{\sigma}\sqrt n) \approx P(\frac{-r}{\sigma}\sqrt n \leq Z \leq \frac{r}{\sigma}\sqrt n) = \Phi(\frac{r}{\sigma}\sqrt n)-\Phi(\frac{-r}{\sigma}\sqrt n)$$
$$= \Phi(\frac{r}{\sigma}\sqrt n)-1+\Phi(\frac{r}{\sigma}\sqrt n)=2\Phi(\frac{r}{\sigma}\sqrt n)-1$$
QUINDI
$$2\Phi(\frac{r}{\sigma}\sqrt n)-1  \geq 1-\delta$$
$$\frac{r}{\hat \sigma}\geq \Phi^{-1}(1-\frac{\delta}{2})$$
Da ciò ricaviamo
$$n \geq \frac{\hat \sigma^2}{r^2}*\Phi^{-1}(1-\frac{\delta}{2})^2$$
$$\delta \geq 2(1-\Phi(\frac{r}{\hat \sigma}*\sqrt n))$$
$$r \geq \frac{\hat \sigma}{\sqrt n}*\Phi^{-1}(1-\frac{\delta}{2})$$
Fissati due valori, posso trovare il terzo
In realta c è anche $\sigma$ MA in realta sarà $\hat \sigma$ stima calcolata a partire dal campione 
SE n risulta basso, avendo applicato il teorema centrale del limite che richiede n grandi, quindi arbitrariamente aumento n