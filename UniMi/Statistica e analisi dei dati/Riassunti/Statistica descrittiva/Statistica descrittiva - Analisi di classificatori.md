Consideriamo un classificatore binario per discriminare tra due classi, positiva e negativa a partire da un insieme di oggetti di cui è noto l'esito della classificazione possiamo valutare la bontà di tale classificatore
- Falso negativo: esempio positivo classificato come negativo
- Falso positivo: esempio negativo classificato come positivo
OSS Non sempre il peso di un falso positivo è lo stesso di un falso negativo

Matrice di confusione mostra il numero di falsi positivi e di falsi negativi unitamente al numero di casi correttamente classificati divisi in veri positivi e veri negativi

|                          |          | Valore effettivo    | Valore effettivo    |                                      |
| ------------------------ | -------- | ------------------- | ------------------- | ------------------------------------ |
|                          |          | Positivo            | Negativo            |                                      |
| Esito del classificatore | Positivo | VP, Veri Positivi   | FP, Falsi Positivi  | TOT CP, totale classificati positivi |
| Esito del classificatore | Negativo | FN, Falsi Negativi  | VN, Veri Negativi   | TOT CN, totale classificati negativi |
|                          |          | TP, Totale Positivi | TN, Totale Negativi | TOT Casi                             |

Indici
- Sensibilità: capacita del classificatore di lavorare con i positivi, $=\frac{VP}{TP}$ 
- Specificità: capacita del classificatore di lavorare con i negativi, $=\frac{VN}{TN}$

Una volta calcolati tali indici consideriamo il punto $(1 - specificità, sensibilità) = (1- \frac{VN}{TN}, \frac{VP}{TP}) = (\frac{FP}{TN} , \frac{VP}{TP})$

Casi particolari
- Classificatori costanti
	- CP associa indiscriminatamente gli oggetti nella classe positiva

|                          |          | Valore effettivo | Valore effettivo |
| ------------------------ | -------- | ---------------- | ---------------- |
|                          |          | Positivo         | Negativo         |
| Esito del classificatore | Positivo | TP               | TN               |
| Esito del classificatore | Negativo | 0                | 0                |

Sensibilità = 1
Specificità = 0
Punto individuato (1, 1)

- CN associa tutti gli oggetti alla classe negativa

|                          |          | Valore effettivo | Valore effettivo |
| ------------------------ | -------- | ---------------- | ---------------- |
|                          |          | Positivo         | Negativo         |
| Esito del classificatore | Positivo | 0                | 0                |
| Esito del classificatore | Negativo | TP               | TN               |

Sensibilità = 0
Specificità = 1
Punto individuato (0, 0)

- Classificatore ideale CI

|                          |          | Valore effettivo | Valore effettivo |
| ------------------------ | -------- | ---------------- | ---------------- |
|                          |          | Positivo         | Negativo         |
| Esito del classificatore | Positivo | TP               | 0                |
| Esito del classificatore | Negativo | 0                | TN               |

Tutti i casi positivi verranno correttamente classificati come anche i casi negativi
Sensibilità=1
Specificità=1

- Classificatore peggiore CE

|                          |          | Valore effettivo | Valore effettivo |
| ------------------------ | -------- | ---------------- | ---------------- |
|                          |          | Positivo         | Negativo         |
| Esito del classificatore | Positivo | 0                | TN               |
| Esito del classificatore | Negativo | TP               | 0                |

- Classificatore casuale

Corrisponde al punto $(\frac{1}{2}, \frac{1}{2})$

|                          |          | Valore effettivo | Valore effettivo |
| ------------------------ | -------- | ---------------- | ---------------- |
|                          |          | Positivo         | Negativo         |
| Esito del classificatore | Positivo | $\frac{TP}{2}$   | $\frac{TN}{2}$   |
| Esito del classificatore | Negativo | $\frac{TP}{2}$   | $\frac{TN}{2}$   |

Sensibilità=0,5
Specificità=0,5

- Classificatori a soglia

Data la posizione del classificatore nel grafico
SE un classificatore restituisce un valore alto, è più sicuro di un risultato e viceversa
Utilizzando delle soglie riesco cosi a binarizzare il risultato date le soglie fissate

Un classificatore a soglia effettua il procedimento di classificazione di un generico oggetto calcolando una quantità e verificando poi che quest'ultima sia superiore a una soglia prefissata

$\forall \Theta \in D$ soglia è possibile calcolare la sensibilità e la specificità del classificatore e disegnare sul piano cartesiano il punto
Il risultato è una traiettoria con estremi 0,0 e 1,1 che prende il nome di curva ROC Receiver Operator Carapteristic

```python
from sklearn.datasets import make_classification
from sklearn.linear_model import LogisticRegression
X, y = make_classification(n_samples=10000, n_features=10, n_classes=2, n_informative=5)
Xtrain = X[:9000]
Xtest = X[9000:]
ytrain = y[:9000]
ytest = y[9000:]
clf = LogisticRegression()
clf.fit(Xtrain, ytrain)
from sklearn import metrics
preds = clf.predict_proba(Xtest)[:,1]
fpr, tpr, _ = metrics.roc_curve(ytest, preds)
plt.plot(fpr, tpr)
plt.plot([0, 1], [0, 1], dashes=[3, 3], color='gray')
plt.xlim([-0.01, 1])
plt.ylim([0, 1.01])
plt.axis('equal')
plt.show()
```

![[Pasted image 20240409100423.png]]

La curva ROC è sempre monotona non decrescente perché all'aumentare della soglia il numero di oggetti classificati positivamente può solo decrescere

Il valore di $\Theta$ può essere scelto in modo da trovare un giusto compromesso tra sensibilità e specificità 

Per misurare la bontà del classificatore indipendentemente dal valore della soglia si calcola l'area compresa tra l'asse delle ascisse e la curva stessa, AUC Area Under the ROC Curve
Si valuta con una discretizzazione dei valori della soglia, approssimando l'area considerando i rettangoli formati
Piu l'area si avvicina a 1, piu il classificatore ha un comportamento che si avvicina al classificatore ideale CI

Caso particolare: classificatori probabilistici che associano a un oggetto una stima delle probabilità che questo appartenga a varie classi

```python
from sklearn import metrics
y = [1, 0, 1, 1, 0]
prob = [.7, .4, .8, .7, .3]
fpr, tpr, _ = metrics.roc_curve(y, prob)
plt.plot(fpr, tpr)
plt.plot([0, 1], [0, 1], dashes=[3, 3], color='gray')
plt.show()
metrics.auc(fpr,tpr)
```

Per calcolare la matrice di confusione: pd.DataFrame(metrics.confusion_matrix(Y_test, preds))

