SE le derivate prime e seconde sono note, si possono enumerare i punti nei quali sono soddisfatte le condizioni analitiche

Gli algoritmi per l'ottimizzazione non lineare sono algoritmi iterativi, che convergono verso un minimo  locale
Partono da una soluzione data $x^{(0)}$ e calcolano una sequenza di soluzioni t.c. il valore di f(x) diminuisca monotonicamente
Si fermano quando il miglioramento ottenuto o il passo compiuto sono piu piccoli di una data soglia

Ad ogni iterazione k, l'algoritmo calcola una direzione $d^{(k)}$ (un vettore) e un passo $s_k$ (uno scalare) t.c. $x^{(k+1)} = x^{(k)} + s_kd^{(k)}$
Caratteristiche che devono avere questi algoritmi
- Convergenza globale: l'algoritmo converge sempre in un minimo locale a partire da qualsiasi punto
Una volta noto che un algoritmo converge in modo globale analizziamo la sua velocita di convergenza
Sia $\{x_k\}$ una sequenza in $R^n$ che converge a $x^*$
- Convergenza lineare: l'errore che commettono rispetto all'iterazione prima è minore di 1
$$\lim _{k-> \infty} \frac{||x_{k+1}-x^*||}{||x_k-x^*||} = r < 1$$
- Convergenza superlineare
$$\lim _{k-> \infty} \frac{||x_{k+1}-x^*||}{||x_k-x^*||} = 0$$
- Convergenza quadratica: considero il quadrato dell'errore dell'iterazione prima (elevando al quadrato è piu piccola perche mi sto avvicinando)
$$\lim _{k-> \infty} \frac{||x_{k+1}-x^*||}{||x_k-x^*||^2} = M$$

Le due principali strategie per costruire algoritmi iterativi che scelgono il passo e la direzione sono
- [[PNL - Line Search]]: prima si sceglie la direzione e poi il passo
- [[PNL - Trust Regions]]: prima si sceglie il passo e poi la direzione

Effetto Scaling
Gli algoritmi di programmazione non lineare possono essere piu o meno robusti rispetto allo scaling (es quando cambio unita di misura di alcune grandezze)
L'invarianza di scala è una proprieta desiderabile degli algoritmi, che li rende appunto piu robusti

