Stratificazione: suddivido il mio campione sulla base di un criterio
- Creo due variabili con le due sottopopolazioni (2 dataframe, quindi due tabelle delle frequenze assolute). Potrebbero avere indici diversi, quindi barre diverse che si potrebbero mescolare in maniera incoerente. Per evitare cio .reindex e .unique
	se ho abc e richiamo reindex con abcd, abc rimangono invariati e viene aggiunta il nuovo indice c
- Calcolo la somma delle frequenze assolute delle due tabelle
- Il grafico ha delle spezzate che pero potrebbero dare un interpretazione sbagliata del grafico, ogni puntino sono degli indici e questi punti vengono uniti da delle righe.

Potrei utilizzare un grafico a barre ma senza nessun accorgimento, invocando due .bar i due grafici si sovrappongono, e di fatto uno potrebbe sovrastare l'altro per alcune barre.

```python
male_strength_freq = (pd.crosstab(index=heroes.loc[heroes['Gender']=='M','Strength'], columns='Rel. freq.', normalize=True).loc[:, 'Rel. freq.'])

female_strength_freq = (pd.crosstab(index=heroes.loc[heroes['Gender']=='F','Strength'], columns='Rel. freq.', normalize=True).loc[:, 'Rel. freq.'])

male_strength_freq.plot(marker='o', color='blue', legend=False)
female_strength_freq.plot(marker='o', color='pink', legend=False)
plt.show()

male_strength_freq.plot.bar(color='blue', alpha=.7)
female_strength_freq.plot.bar(color='pink', alpha=.7)
plt.show()
```

es
![[Pasted image 20240401185027.png]]
