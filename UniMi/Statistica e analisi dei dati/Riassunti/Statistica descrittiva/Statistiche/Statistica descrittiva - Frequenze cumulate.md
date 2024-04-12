Le frequenze cumulate si ottengono calcolando le frequenze dei valori ordinati dal piu piccolo al piu grande e di cumularle in modo che al primo elemento sia associata la sua frequenza e che all'elemento i-esimo sia associata la somma delle frequenze di tutti i valori precedenti nell'ordine di i
Si possono calcolare solo quando esiste una relazione d'ordine per i valori del carattere
Per calcolarle invochiamo il metodo cumsum su una serie o su un dataframe in cui risulta piu comodo data la tabella delle frequenze gia ordinate di default
```python
first_app_freq_cumulate = (pd.crosstab(index=heroes_with_year['First appearance'], columns=['Cumulate freq.'], colnames=['']).cumsum())
```

Rappresentando le frequenze cumulate con .plot notiamo che il grafico è monotono crescente con i valori che variano da 0 al totale dei casi del dataset
Il grafico delle frequenze cumulate ci permette di trovare facilmente la mediana (con normalize=True) e di conseguenza tutti i decili/centili
Anche in questo caso potrei avere delle spezzate date dalla mancanza di dati.
```python
first_app_freq_cumulate.plot(marker='o', legend=False)
plt.show()
```
Possiamo considerare anche le frequenze relative cumulate con valori da 0 a 1
```python
first_app_relfreq_cumulate = (pd.crosstab(index=heroes_with_year['First appearance'], columns=['Cumulate freq.'], colnames=[''], normalize=True).cumsum())
first_app_relfreq_cumulate.plot(legend=False)
plt.show()
```

OSS il grafico prodotto è lineare / costante a tratti, cioe è una sequenza di segmenti in cui ogni elemento ha l'estremo destro coincidente con quello sinistro del segmento successivo

[[Funzione cumulativa empirica]]