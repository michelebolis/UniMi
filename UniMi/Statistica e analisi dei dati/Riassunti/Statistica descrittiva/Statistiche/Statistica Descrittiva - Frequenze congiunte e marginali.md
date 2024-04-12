Il concetto di frequenza si può declinare anche per coppie di valori
Consideriamo due attributi invece di uno per verificare se essi siano piu o meno collegati con una relazione
La frequenza congiunta assoluta puo essere rappresentata in una tabella delle frequenze congiunte (SE il numero di osservazioni è ridotto) in cui ogni riga rappresenta i possibili valori di uno dei due caratteri, che saranno presenti nelle colonne

Per generare questa tabella utilizziamo pd.crosstab specificando oltre all'index anche columns

```python
int_gender_freq = pd.crosstab(index=heroes['Intelligence'], columns=heroes['Gender'])
int_gender_freq
```

![[Pasted image 20240408143928.png]]

Pero i valori delle frequenze non sono ordinati, in quanto di default c è l'ordine alfabetico
- L'ordine delle righe puo essere cambiato con reindex passandogli la lista dei valori nell'ordine desiderato
- L'ordine delle colonne puo essere cambiato con loc specificando la lista dei caratteri nell'ordine (`.loc(:, [carattere1, carattere2]]`)
OSS è possibile considerare solo alcune righe usando la loc MA non sarebbe piu una tabella delle frequenze perche escludo delle frequenze

```python
int_gender_freq.loc['moderate':'good', :]
```

Rappresentiamo graficamente la tabella con plot.bar in modo che le barre dei due caratteri risultino affiancate mentre specificando stacked=True risulteranno sovrapposte

```python
int_gender_freq.plot.bar(color=['pink', 'blue'], stacked=True)
plt.show()
```

Considerando il caso di almeno uno dei due caratteri di tipo numerico, si riscontrerebbero gli stessi problemi dell'istogramma
Usando pd.cut convertiamo la nostra serie di valori numerici in una serie qualitativa i cui valori possibili sono intervalli di una partizioni aventi come estremi i valori, eventualmente specificati nell'argomento bins
Di default gli intervalli sono (…, …] ma si possono invertire con right=False

```python
pd.crosstab(index=pd.cut(heroes['Weight'], bins=[30, 50, 80, 100, 200, 500, 1000], right=False), columns=[heroes['Gender']])
```

Se invece di considerare attributi categorici, considero attributi numerici (eventualmente float) potrei avere ancora problemi di molti valori distinti per poco. E' necessario quindi aggregarli come nell'istogramma
Pre processing dell'attributo weight: come argomento di crosstab index uso `pd.cut(serie, bin=[30, 50, …,])` specificando i bin
Escono intervalli aperti e chiusi per evitare che un valore venga contato più di una volta

Specificando l'argomento margins=True, si aggiunge una riga e una colonna con i totali rispettivamente delle colonne e delle righe. Questi valori prendono il nome di frequenze marginali

```python
pd.crosstab(index=heroes['Intelligence'], columns=heroes['Gender'], margins=True)
```
![[Pasted image 20240408144111.png]]

Specificando l'argomento normalize='…' trasformiamo le frequenze assolute in relative in particolare
- normalize='all' vengono calcolate le frequenze relative
- normalize='index' i valori su ogni riga sommati danno 1, normalizza per riga
- normalize='columns' i valori sulle colonne sommati danno 1, normalizzo per colonna