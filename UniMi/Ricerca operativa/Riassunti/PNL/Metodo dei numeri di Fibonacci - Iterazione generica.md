Alla generica iterazione $k$, si ha un intervallo di incertezza $I^k$
Si considerano due punti $a^k$ e $b^k$ interni all'intervallo che lo dividono in tre parti
Si conosca il valore della funzione $f(x)$ nei due punti interni
- SE $f(a^k) > f(b^k)$, ALLORA il minimo $f(x)$ non cade nella prima parte
- SE $f(a^k) < f(b^k)$, ALLORA il minimo $f(x)$ non cade nella terza parte

![[Pasted image 20240401102743.png|250]]

Alla successiva iterazione l'intervallo di incertezza risulta composta da due delle tre parti dell'intervallo di incertezza precedente e uno dei due punti interni diventa un estremo dell'intervallo di incertezza

Per simmetria, ad ogni iterazione i punti in cui valutare $f(x)$ sono scelti in modo simmetrico nell'intervallo di incertezza corrente
Proprieta che ne consegue:
$$I^k=I^{k+1}+I^{k+2}, \forall k \geq 0$$
![[Pasted image 20240401103045.png|250]]

OSS in uno dei due punti interni la funzione è gia stata valutata in precedenza
