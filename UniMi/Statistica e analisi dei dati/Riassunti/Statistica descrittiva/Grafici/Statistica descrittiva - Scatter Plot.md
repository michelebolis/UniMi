Considerando due serie con un medesimo indice, individuiamo un punto sul piano dato dai valori delle due serie. Oppure considerando una riga fissata, quindi un individuo, voglio analizzare la relazione tra due attributi dell'individuo
Ripetendo la stessa cosa per tutti gli individui, otteniamo una nuvola di punti
Abbiamo otteniamo un diagramma di dispersione o scatter plot

NON sto cercando una relazione deterministica, ma una tendenza
SE esistesse una qualunque relazione lineare, otterrei esattamente una retta congiungendo i punti

Generiamo uno scatter plot da un dataframe invocando plot.scatter() indicando come argomenti i nomi dei caratteri da considerare

```python
heroes[heroes['Gender']=='M'].plot.scatter('Height', 'Weight')
plt.show()
```

Semplice estrapolare (una volta compresa la relazione) cioè trovare la retta che minimizza la distanza tra i punti usando il machine learning di sklearn