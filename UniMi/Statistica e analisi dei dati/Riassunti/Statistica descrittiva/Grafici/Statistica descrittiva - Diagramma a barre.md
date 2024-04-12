Per rappresentare graficamente la tabelle delle frequenze, utilizzo plot.bar() ottenendo un diagramma a barre
- SE utilizzo plot.bar su value.counts ottengo un ordinamento non crescente sulle frequenze
- SE utilizzo plot.bar sul dataframe ottengo un ordinamento in base ai valori e una legenda dell'asse delle ascisse (che si puo togliere con legend=False)
Il diagramma a barre opportuno per gli indici (asse delle x) con attributo qualitativo pero non ordinato
Se invece l attributo fosse quantitativo sarebbe forviante

Come prima, per cambiare l'ordine in cui sono visualizzate le barre uso loc
```python
publisher_order = ['Hanna-Barbera', 'ABC Studios', 'Dark Horse Comics',
                   'Image Comics', 'Marvel Comics', 'DC Comics',
                   'George Lucas', 'Rebellion',
                   'Star Trek', 'Universal Studios']
publisher_rel_freq.loc[publisher_order,:].plot.bar(legend=False)
plt.show()
```
La frequenza relativa di un valore è la rappresentazione di quella assoluta in modo frazionato
L'uso delle frequenze relative permette di confrontare situazioni in cui il numero di osservazioni è variabile
Frequenze relative permette di ragionare considerando delle sottopopolazioni della popolazione
Utilizzando le frequenze relative ha quindi senso sovrapporre grafici di diversi valori