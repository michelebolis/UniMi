Ogni misurazione ha una certa incertezza
Come calcolare la taglia di un campione
- Utilizzo [[Statistica Inferenziale - TCL Teorema centrale del limite]]
- Utilizzo [[Statistica Inferenziale - TCH Chebyshev]]

Quale è la strategia migliore?
$TCL \leq RCH$
$$\frac{\hat \sigma^2}{r^2}*\Phi^{-1}(1-\frac{\delta}{2})^2 \leq \frac{\sigma^2}{\delta r^2}$$
$$\delta\Phi^{-1}(1-\frac{\delta}{2})^2\leq 1$$
$$1-\frac{\delta}{2}\leq \Phi(\frac{1}{\delta})$$

TCL trova sempre un n minimo piu basso, ragionevole perche Chebyshev è una disuguaglianza altamente generale e a volte il lower bound non è informativo