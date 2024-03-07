Variazione di un coefficiente $c_j$
Intuizione geometrica
![[Pasted image 20240305133849.png|400]]
![[Pasted image 20240305141057.png|200]]
Quando $c_1$ diminuisce, pesa meno nella funzione obiettivo, tanto che per $c_1 = 1$ la base ottima cambia
Quando $c_1$ aumenta, le curve di livello tendono a diventare verticali per $c_1 -> \infty$ e quindi la base ottima non cambia

$B^* = \{1, 2, 3\}$ è ottima per $1 \leq c_1 < \infty$
OSS anche se $B^*$ e $x^*$ non cambia, $z^*$ cambia

Supponiamo di analizzare un problema che nella forma alle disuguaglianze ha 
- funzione obiettivo da massimizzare 
- vincoli di disuguaglianza $\leq$

Considerando la colonna $\bar{j}$ e $\Delta c_{\bar{j}}$ la variazione possibile
1. $\bar{j} \in B$ e $\bar{r}$ è la riga corrispondente
$$\max\{-\infty, \max_{j \in N}\{\frac{-c_j^*}{a^{*+}_{\bar{r}j}}\}\} \leq \Delta c_{\bar{j}} \leq \min\{\min\{\frac{-c_j^*}{a^{*+}_{\bar{r}j}}\} + \infty\}\}$$
Interpretazione: per i valore negativi (numeratore negativi e denominatore positivo) cerchiamo il max mentre di quelli positivi il min, che sono i primi valori che ci fanno cambiare base
2. $\bar{j} \in N$
$$\Delta c_{\bar{j}} \leq c^*_{\bar{j}}$$

Esempio
![[Pasted image 20240305140729.png|400]]
