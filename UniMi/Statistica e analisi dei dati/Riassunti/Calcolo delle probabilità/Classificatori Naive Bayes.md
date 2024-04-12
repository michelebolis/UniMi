Osserviamo in una serie di individui la presenza / assenza di una proprietà ottenendo un'osservazione $x_i\in \{0,1\}$
Cerco di predire un attributo a partire da un altro ma in realtà sono interscambiabili dato il teorema di Bayes
Dato un individuo assocerà ad ognuna delle classi una probabilità
Stiamo ancora lavorando in termini binari, sia per il risultato della classe che per l attributo che analizzo

Es voglio predire l editore dell'eroe dato il fatto che l eroe abbia gli occhi neri
Scambiamo l evento condizionato con l evento condizionante
$P(M | N)= \frac{P(N | M)*P(M)}{P(N)}$
Relazione tra probabilità e frequenza relativa all interno di un dataset (frequenza approssima probabilità ed è tanto migliore tanto è grande il dataset)

- $P(N | M)$ può essere approssimata calcolando la frequenza relativa con cui un supereroe Marvel ha gli occhi neri

```python
blackeyes_and_marvel_heroes = heroes[(heroes['Publisher']=='Marvel Comics') & \(heroes['Eye color']=='Black')]
p_blackeyes_given_marvel = len(blackeyes_and_marvel_heroes) / len(marvel_heroes)
```

- $P(M)$ può essere approssimata calcolando la frequenza relativa con cui un supereroe è Marvel

```python
marvel_heroes = heroes[heroes['Publisher']=='Marvel Comics']
p_marvel = len(marvel_heroes) / len(heroes)
```

- $P(N)$ può essere approssimata calcolando la frequenza relativa con cui un supereroe ha gli occhi neri

```python
black_eyes_heroes = heroes[heroes['Eye color']=='Black']
p_blackeyes = len(black_eyes_heroes) / len(heroes)
p_blackeyes_given_marvel * p_marvel / p_blackeyes
```

Lo faccio perché magari l'attributo (l'editore) è mancante ma il colore degli occhi è presente, faccio un imputazione dei valori mancanti

Complemetando $M$ avrei ottenuto il complemento di $P(M | N)$
Oltre al colore degli occhi potrei considerare altri attributi

Consideriamo due attributi stavolta non binari
Estendo sia gli attributi che i casi dei possibili valori

$$P(M | O=o_i \cap C=c_j) = \frac{( P(O=o_i \cap C=c_j | M)*P(M) )}{P(O=o_i \cap C=c_j))}$$
Cambia dal punto di vista dell'efficienza
Naive Bayes perché semplifica, invece che il prodotto dei valori possibili per il numero di attributi, $P(O=o_i ∩ C=c_j | M)$ viene approssimato come $P(O=o_i | M)*P(C=c_j |M)$ cioè dato $M$, stiamo dicendo che $O$ e $C$ sono indipendenti, assunzione sull'indipendenza ingenua, Naive.
Al numeratore della frazione potremo avere al massimo $m + n$ diverse probabilità al posto di $m * n$

$$P(M | O=neri \cap C=neri) \approx \frac{P(O=neri |M) * P(C=neri | M)}{P(O=neri \cap C=neri))}$$

Per estendere come ragionamento al caso in cui un attributo non sia solo due possibilità (es editore marvel vs dc)
$$P(E=e_k | O=o_i \cap C=c_j) \approx \frac{( P(O=o_i | E=e_k) * P(C=c_j | E=e_k) )}{ P(O=o_i \cap C=c_j ))}$$

Il denominatore sarà sempre uguale
Ma dato che mi interessa $e_k$ che massimizza non considero il denominatore

Generalizzando
Per un dato individuo si vogliono osservare congiuntamente i valori $x_1, …, x_n$ per $n$ proprietà $X_1, …, X_n$ e denotiamo con $X_1 = x_1, …, X_n = x_n$ gli eventi corrispondenti
Supponiamo che vi siano $m$ possibili classi che corrispondono agli eventi $Y = y_1, …, Y = y_m$
Per ognuna di queste classi vorremmo calcolare e assegnare l'individuo alla classe per cui massimizza tale probabilità

$$P(Y=y_k|X_1=x_1,...,X_n=x_n) = \frac{P(X_1=x_1 \cap ... \cap X_n=x_n|Y=y_k)*P(Y=y_k)}{P(X_1=x \cap ... \cap X_n=x_n)}$$
$$P(Y=y_k|X_1=x_1,...,X_n=x_n) \approx \frac{\sum_{i=1}^n P(X_i=x_i|Y=y_k)*P(Y=y_k)}{P(X_1=x \cap ... \cap X_n=x_n)}$$
$$k^*=  argmax_kP(Y=y_k)\prod_{i=1}^n P(X_i=x_i|Y=y_k)$$
Per calcolare ciò utilizziamo sklearn
Richiesta: dati completamente specificati, no dati mancanti : uso .dropna
Richiesta: solo attributi numerici (costruivamo un mappaggio)
Poi problema magari alcuni numeri sono continui mentre altri discreti quindi ci potrebbero essere problemi coi filtri quindi raggruppiamo
Ovviamente dovremmo lavorare sul dataframe ma ciò è pericoloso quindi è meglio fare una copia su cui lavorare

qcut per fare binning che facevo nell'istogramma ma lavorando con i quantili

In sklearn ci sono alcune finezze possibili
In funzione del modo in cui faccio la stima delle probabilità ho modi diverse,
GaussianNB assume che i dati seguano una distribuzione di probabilità
sklearn ha un interfaccia coerente con i metodi definiti nella classe padre

.fit(righe del dataframe, etichette) addestro
Con .predict(X) ottengo un array con 1 predizione positiva
`.predict(X[Y==0])` righe del dataframe che corrispondono ai casi non positivi SE classificatore è buono mi aspetto tanti 0
Se ci sono tanti 1 ho un falso positivo

Posso calcolare i true positive e tutti gli altri ottenendo la matrice di confusione