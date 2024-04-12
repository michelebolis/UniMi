Le frequenze assolute/relative e cumulate di una variabile categorica possono essere considerate congiuntamente generando un diagramma di Pareto, ordinando i dati per frequenza decrescente su uno stesso sistema di riferimento in cui l'asse delle ascisse fa riferimento ai valori.
In questo sistema si sovrappongono il diagramma a barre delle frequenze assolute/relative e la linea spezzata he collega i valori delle frequenze cumulate

```python
eye_color = heroes['Eye color']
eye_color_freq = eye_color.value_counts(normalize=True)
eye_color_freq[eye_color_freq>.02].cumsum().plot()
eye_color_freq[eye_color_freq>.02].plot.bar()
plt.show()
```

La linea spezzata non arriva sempre all'ordinata 1 (considerando le frequenze relative) in quanto consideriamo solo un sottoinsieme dei dati dato il possibile gran numero di dati con una frequenza bassa e quindi trascurabile
Voglio pero considerare un sottoinsieme del mio campione, per avere una risposta succinta non considero quindi tutti i valori distinti il cui numero potrebbe essere molto elevato ma con molti valori con una frequenza relativa trascurabile

Per far arrivare il diagramma di Pareto fino all'ordinata unitaria si attua una normalizzazione in particolare dividiamo tutte le frequenze per la sommatoria
La normalizzazione tipicamente si ottiene
- dividendo per la somma, in modo che i dati trasformati hanno somma 1
- dividere per il massimo, in modo che i dati trasformati siano <1

```python
norm_eye_color_freq = eye_color_freq[eye_color_freq>.02]/sum(eye_color_freq[eye_color_freq>.02])
norm_eye_color_freq.cumsum().plot()
norm_eye_color_freq.plot.bar()
plt.show()
```

![[Pasted image 20240408143737.png]]

In generale un diagramma di Pareto permette di identificare gli elementi piu rilevanti in termini di frequenze all'interno di un insieme di osservazioni
Tuttavia dobbiamo considerare che non stiamo tenendo in considerazione tutte le osservazioni, considerandole tutte pero uscirebbe un grafico poco leggibile

```python
def my_pareto(data, threshold=0.02, renormalize=False):
    freq = data.value_counts(normalize=True)
    freq = freq[freq > threshold]
    if renormalize:
        freq = freq / sum(freq)
    freq.cumsum().plot()
    freq.plot.bar()
my_pareto(heroes['Eye color'], threshold=0)
```
