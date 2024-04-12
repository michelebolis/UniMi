Per rappresentare graficamente le tabelle delle frequenze di dati quantitativi, usiamo ancora plot.bar
Tuttavia è molto probabile che il risultato non sia ottimale in quanto le barre hanno uno spessore che puo suggerire un interpretazione fuorviante secondo cui le frequenze non facciano riferimento ad un anno MA a un intervallo
```python
first_app_freq = heroes_with_year['First appearance'].value_counts()
plt.bar(first_app_freq.index, first_app_freq.values)
plt.show()
```
Si utilizza in questi casi un grafico a bastoncini in cui ogni punto è evidenziato da un segmento verticale che lo congiunge con l'asse delle ascisse. Lo si genera con plt.vlines(listaIndici, yiniziale, listaValori)
Eventualmente si puo sovrapporre con un plt.plot che rappresenta un cerchio

```python
plt.vlines(first_app_freq.index, 0, first_app_freq.values)
plt.show()
```

Ulteriore problema che ricorre spesso nel dati quantitativi sono i numerosi valori distinti per un valore piccolissimo es 81.01 e 81
Risulta piu sensato calcolare le frequenze di intervalli di possibili valori, aggregando quindi i valori MA non sarebbe corretto perché daremmo l impressione che un certo valore ha una frequenza alta

Alcuni insiemi hanno troppi valori distinti per poter usare il metodo del grafico poligonale/a barre. Suddividiamo i valori in gruppi/classi e poi rappresentiamo con un grafico il numero di valori dei dati appartenenti a ciascuna classe

Come scegliere li numero di classi:
- SE troppo poche classi, perdo molte informazioni sui valori effettivi
- SE troppe classe, ottengo frequenza troppo basse per ottenere delle informazioni dal grafico
Di solito si scelgono tra le 5 e le 10 classi. Prassi scegliere classi della stessa lunghezza
I valori al bordo di una classe di chiamano estremi della classe.
Convenzione di inclusione a sinistra: classe include il suo estremo sinistro ma non quello destro

Utilizziamo quindi un istogramma, generabile con .hist()
Come argomento a hist possiamo specificare i bins, cioe i sotto intervalli espressi o come differenza tra gli intervalli
.hist() in modo automatico raggruppa i dati, calcola le frequenze e lo rappresenta
es bins=50 oppure come con np.stack((np.arange(0, 200, 20)), …) posso specificare gli intervalli
np.hstack permette di giustapporre due o piu array numpy mentre np.arange permette di creare un array con valori che variano tra i primi due argomenti secondo il terzo argomento

```python
heroes['Weight'].hist(bins=50)
plt.show()
heroes['Weight'].hist(bins=np.hstack((np.arange(0, 200, 20),
                                      np.arange(200, 500, 50),
                                      np.arange(500, 1000, 100))))
plt.show()
```

OSS nell'istogramma è l'area di ogni barre a essere legata alla frequenza
SE le barre hanno basi della stessa lunghezza, le aree sono proporzionali all'altezza

es
![[Pasted image 20240401185324.png]]
