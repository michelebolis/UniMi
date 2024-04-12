Vorrei poter sapere se due campioni sono provenienti dallo stesso fenomeno.
- Per far ciò confronto le due medie, se sono simili non ho la garanzia che siano dello stesso fenomeno come anche la moda e la mediana.
- SE invece considero tutti i quantili ho la garanzia, pero non posso calcolarli tutti.
- Se calcolo i percentili, se a parità di livello sono vicino, posso dire che le popolazioni sono le stesse

Un diagramma Q-Q / Quantile-Quantile è una rappresentazione grafica utilizzata per verificare se due campione seguano una medesima distribuzione
Ogni asse lo associo con un campione, segnando i punti come incontro dei due percentili. Prendendo come riferimento la bisettrice del primo e del terzo quadrante, se i punti sono vicini ad essa, allora posso dire che la popolazione è plausibilmente la stessa
Questi diagrammi si basano sul fatto che i quantili campionari rappresentano l'approssimazione di quantili teorici che considerandoli tutti individuano univocamente la distribuzione dei dati
SE due campioni hanno un'uguale distribuzione ALLORA estraendo da entrambi il quantile di un livello si dovranno ottenere due numeri molto vicini

---

Per ottenere il Q-Q facciamo variare i livello nell'intervallo [0, 1] con np.linspace(0, 1, 100) e utilizziamo tali livelli in .quantile(levels) ottenendo i punti sul piano.
Considerando la bisettrice del primo e del terzo quadrante, ottenibile con un plot che considera i due punti (min, min) e (max, max) (ottenibili con .plot([min, max], [min, max])), se i quantili sono molto simili, saranno molto vicini alla bisettrice

---

Per ottenere il Q-Q utilizziamo il package statsmodels.api as sm invocando il metodo sm.qqplot_2samples specificando le due serie e line='45 per evidenziare la bisettrice

```python
import statsmodels.api as sm
sm.qqplot_2samples(marvel_sample, dc_sample, line='45')
plt.show()
```

OSS non è detto che due campioni seguano una stessa distribuzione: il Q-Q permette di confutare l'ipotesi di medesima distribuzione
OSS normalizzando i dati si possono notare piu facilmente valori fuori scala

| Caso medesima distribuzione          | Caso diversa distribuzione           |
| ------------------------------------ | ------------------------------------ |
| ![[Pasted image 20240408150757.png]] | ![[Pasted image 20240408150800.png]] |
Oltre a mostrare il comportamento relativo di due variabili ed aiutarci nella rappresentazione, è utile per riconoscere i valori anomali/outliner, punti che non seguono il comportamento degli altri. Una volta identificati possiamo decidere quali siano appropriati e quali siano invece causati da errori nella raccolta dei dati