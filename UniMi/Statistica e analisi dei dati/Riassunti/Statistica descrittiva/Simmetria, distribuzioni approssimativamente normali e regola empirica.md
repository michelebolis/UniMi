Quando le frequenze tendono a distribuirsi in modo simmetrico rispetto al valore della media campionaria si dice che il campione segue una distribuzione approssimativamente simmetrica
La simmetria è visibile sia nei diagrammi a barre/istogramma che nel box plot

L'asimmetria si puo presentare in due diverse modalità
- Skew a destra: presenta un coda nella parte di destra cioe presenta valori piu basse delle frequenze nella parte destra e da un baffo destro piu lungo nel box plot
- Skew a sinistra

Una distribuzione è approssimativamente normale SE la simmetria è accompagnata da una forma a campana del grafico delle frequenze in cui i dati si concentrano attorno alla media campionaria secondo la regola empirica

- approssimativamente il 68% delle osservazioni dista dalla media campionaria non più di una deviazione standard campionaria; $\overline x \pm \sigma$ 
- approssimativamente il 95% delle osservazioni dista dalla media campionaria non più di due deviazioni standard campionarie; $\overline x \pm 2\sigma$ 
- approssimativamente il 99.7% delle osservazioni dista dalla media campionaria non più di tre deviazioni standard campionarie. $\overline x \pm 3\sigma$ 

Possiamo controllare questa regola definendo una funzione check_empirical_rule(n) con n il coefficiente da applicare alla deviazione standard campionaria

```python
def check_empirical_rule(n):
    within = len(sample[np.abs(sample - sample.mean()) < n*sample.std()])
    return  within / len(sample)
pd.DataFrame([check_empirical_rule(n) for n in range(1, 4)], columns=['%'], index=range(1, 4))
```

Considerando un istogramma, l'andamento dei dati può essere unimodale, cioè andamento rispetto alle x tende a crescere fino a un massimo e poi decrescere.
L'andamento può essere lineare o meno
Questo andamento a campana / curva gaussiana/normale tende a emergere naturalmente

Proprietà che ne conseguono:
- Allineando l'istogramma con un box blot, la mediana è allineata con la moda e si nota una certa simmetria nel box plot. Media, mediana e moda tendono ad assumere lo stesso valore SE ho la simmetria e l unimodalità

| Distribuzione simmetrica             | Coda a destra                        | Coda a sinistra                      |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| ![[Pasted image 20240408150615.png]] | ![[Pasted image 20240408150617.png]] | ![[Pasted image 20240408150620.png]] |
