Un grafico alternativo per le frequenze dei valori qualitativi, è l'areogramma / diagramma a torta generabile con il metodo pie. Un cerchio è diviso in tanti settori le cui aree sono proporzionali alle frequenze
```python
gender_freq.plot.pie(y='Abs. frequence', colors=['pink', 'blue'])
plt.show()
```

Osservazioni:
- plot.bar è in grado di visualizzare piu caratteri contemporaneamente mentre plot.pie solo uno. In entrambi in casi dovrò estrarre la/le serie dal dataframe
- Quando si costruisce un grafico a barre per un carattere ha senso usare un solo colore

![[Pasted image 20240401185125.png]]

