Il box plot / diagramma a scatola è una rappresentazione grafica che riassume le principali caratteristiche di un campione.
Questa rappresentazione è composta da
- Una scatola (un rettangolo) che evidenzia il primo e il terzo quartile in corrispondenza delle due basi mentre la mediana è indicata da un segmento parallelo alle basi
- Due baffi che si estendono dagli estremi della scatola, dal massimo al minimo
Considerando: MIN - primo quartile - Mediana - terzo quartile - MAX

Il box plot permette di evidenziare la centralità delle osservazioni e la loro dispersione in termini di range interquartile, cioè l'estensione della box, e di intervallo di variazione dei dati / range, definito come la distanza tra MAX e MIN

```python
year.plot.box(whis='range')
plt.show()
```

OSS di default il box plot analizza ed esclude gli outliner, per evitare cioe specifichiamo l'argomento whis='range'
Un valore è un outliner SE la sua distanza dalla mediana è più di una costante moltiplicata per il range interquartile
Per visualizzare il box plot in modo orizzontale usiamo vert=False