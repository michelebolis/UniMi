Le funzioni non differenziabili hanno derivate direzionabili: data una funzione $f(x)$ e una direzione $p$, la derivata direzionale di $f(x)$ nella direzione $p$
$$D(f(x), p) = \lim_{\epsilon->0}\frac{f(x+\epsilon p)-f(x)}{\epsilon}$$
Quando $f(x)$ è continua e differenziabile in un intorno di $x$ si ha corrispondenza con il gradiente
$$D(f(x),p) = \bigtriangledown f(x)^Tp$$
In un metodo line search, la condizione per accettare un passo $\alpha$ è che sia abbastanza piccolo affinché sia soddisfatta per qualche $0 \leq \eta \leq 1$
$$\phi(x+\alpha p, \mu) \leq \phi(\mu, x) + \eta\alpha D(\phi(x,u), p)$$
Il nuovo punto che raggiungeremmo dopo il passo valutato con la funzione di merito deve essere minore o uguale al valore della funzione di merito dove siamo ora, sommata alla derivata direzionale nel punto in cui siamo e in p (quanto promette di migliorare se ci muoviamo per p) moltiplicata per $\alpha$

I metodi trust region usano tipicamente un modello quadratico $q$ per stimare il valore di $\phi$ dopo un passo $p$
La condizione sufficiente per accettare il passo. per qualche $0 \leq \eta \leq 1$, è 
$$\phi(x + p, \mu) \leq \phi(x, \mu)-\eta(q(0)-q(p))$$
In questo caso ci chiediamo quanto è il miglioramento quadratico spostandosi di $p$ 
