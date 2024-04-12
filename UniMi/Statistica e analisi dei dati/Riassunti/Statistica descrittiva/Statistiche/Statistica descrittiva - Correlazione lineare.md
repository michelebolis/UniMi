Relazione diretta quando con valori elevati di un attributo, anche l'altro attributo è grande
Relazione indiretta il valore basso di un attributo corrisponde ad un valore alto dell'altro e viceversa

OSS le relazioni dirette/indirette non sono necessariamente lineari es logaritmica

Una volta ottenuta la retta che modella la relazione tra i due attributi (riesco a descrivere la relazione ma perdo del dettaglio), posso fare estrapolazioni in particolare anche di punti non presenti nel campione

Casistiche:
- SE dato un valore di x, ottengo diversi valori di y, si dice che non c è una relazione / c è indipendenza
- SE ottengono una relazione che nel mondo fisico non esiste:
	- Relazione supportata dai dati semplicemente nessuno la conosceva
	- Abbiamo pochi dati
	- Abbiamo fatto degli errori

Es correlazione vendite dolci e torce elettriche solo in luoghi con uragani

Esprimere la relazione tra due attributi in termini quantitativi
Considerando la relazione diretta, con campione di coppie $x_1, …, x_n$ e $y_1, …, y_n$
- O $x_i$ è piccolo e $y_i$ è grande
- O $x_i$ è grande e $y_i$ è grande

Utilizziamo come termine di paragone la media campionaria $\overline x$ e $\overline y$  

- Un valore è da considerarsi piccolo SE $x_i < \overline x$  
- Un valore è da considerarsi grande SE $x_i > \overline x$ 

Quindi 
$$((x_i-\overline x)\leq 0\wedge(y_i-\overline y)\leq 0))\vee (x_i - \overline x) > 0 \wedge (y_i - \overline y) > 0 ))$$

$(x_i - \overline x) * (y_i - \overline y)\geq 0$ in qualunque caso dei due mi trovi

Per controllare la relazione diretta nella maggiore parte dei casi, sommo il prodotto per tutti gli $i=1, …, n$ e se la somma sarà positiva, allora la relazione è diretta, viceversa sarà indiretta se la somma è negativa

Covarianza campionaria
$$COV = \frac{1}{n-1}*\sum_{i=1}^n(x_i - \overline x) * (y_i - \overline y)$$
SE $COV \geq 0$ relazione tendenzialmente diretta
SE $COV<0$ relazione tendenzialmente indiretta

Per calcolare covarianza richiamo cov sulla serie che contiene un attributo 

Indice di correlazione lineare "rho" 
$$\rho(x,y)= \frac{COV(x,y)}{\sigma_x\sigma_y}$$
Una relazione diretta / indiretta potrebbe essere più che tendenziale, ma lineare
La relazione è lineare SE $\exists a, b \in R | y_i= a + b * x_i$

In questo caso la media campionaria di $y$ si ottiene applicando $a$ e $b$ nello stesso modo alla media campionaria di $x$
$$\overline y = a+b \overline x$$
$$s_y = |b| * s_x$$

$$COV(x, y)=\frac{1}{n-1}*\sum_{i=1}^n(x_i-\overline x)*b*(x_i-\overline x)=\frac{b}{n-1}*\sum_{i=1}^n(x_i-\overline x)^2=\rho*\sigma_x^2$$
$$\rho(x, y)= b * \frac{\sigma_x^2}{\sigma_x *|b|* \sigma_x} = \frac{b}{|b|} = \begin{cases} 1 \text{ SE } b<0 \\ -1 \text{ SE } b>0 \end{cases}$$
ATT $s_x^2$ NON è $s_x * s_x$, sono nomi di due cose diverse

QUINDI SE $\rho = 1$ vuol dire che la relazione linearmente diretta mentre
SE $\rho = -1$, allora la relazione è linearmente indiretta

Proprieta
- Si può dimostrare che $\rho$ è sempre compreso tra -1 e 1
- Piu sono vicino a 1, più la nuvola di punti si distribuirebbe vicino a una retta con il coefficiente angolare positivo
- $\rho$ non dipende dall'unita di misura scelta

Calcolando invece la covarianza campionaria, questo può essere un numero qualunque di cui l'unica discriminante è il segno.
ATT $\rho$ non cattura tutte le relazioni dirette e indirette ma SOLO quelle lineari
$\rho$ è insensibile alle alterazioni lineari
ATT non è detto che se misuro la covarianza o $\rho$ e mi escono vicino a 0, questo NON implica ho indipendenza