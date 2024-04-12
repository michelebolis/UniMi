Frequenze assolute: conteggio del numero di volte che una data osservazione occorre in un campione, numero di xi uguali a quel valore
Facile analizzare la frequenza assoluta di dati qualitativi
Il campione non è descritto in modo estensivo ma con la tabella delle frequenze
```python
heroes_with_year['Publisher'].value_counts()
```
Rappresentiamo le frequenze assolute nella tabella delle frequenze assolute attraverso value_counts oppure con pd.crosstab, che ha come argomento index la serie su cui calcolare le frequenze, rappresentando un dataframe su cui possiamo eventualmente eseguire operazioni come quella di slicing

E' possibile trasformare la tabella delle frequenze assolute nella tabella delle frequenze relative specificando l'argomento opzionale normalize=True
```python
publisher_freq = pd.crosstab(index=heroes_with_year['Publisher'],
                             columns=['Abs. frequence'],
                             colnames=[''])
```

Pero le frequenze relative hanno molti numeri dopo la virgola irrilevanti
Possiamo poi migliorare la visualizzazione delle frequenze relative arrotondandole usando .apply
OSS apply su TUTTE le colonne (in questo caso ne abbiamo solo 1)

```python
publisher_rel_freq.apply(lambda p: 100 * np.round(p, 3))
```

Eventualmente per aggiungere il %:
```python
(publisher_rel_freq.apply(lambda p: np.round(100*p, 2))
                   .astype(str)
                   .apply(lambda s: s + '%'))
```

np tende a rimplementare le funzioni in modo vettoriale, cioè specificando una struttura dati, la funzione viene applicata elemento per elemento
Pandas di solito non lavora in place ma restituisce qualcosa

L'ordine delle righe della tabella sarà l'ordinamento predefinito non decrescente dei suoi elementi
Nel caso volessi cambiare tale ordinamento, useremo la proprieta loc del dataframe specificando una lista dei valori nell'ordine desiderato
```python
gender_freq.loc[['M', 'F']]
```

