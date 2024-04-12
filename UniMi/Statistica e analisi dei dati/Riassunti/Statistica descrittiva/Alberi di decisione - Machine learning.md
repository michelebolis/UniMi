Problema della classificazione: ogni oggetto è descritto per una serie di attributi, voglio assegnare ogni oggetto ad ogni categoria
Costruire l'albero in modo dinamico dalla radice:
Quale criterio uso per valutare la bontà delle domande che pongo?
Vedo come si dividono i campioni in base alla risposta SI/NO della domanda fissata, calcolo l'eterogeneità per i due gruppi che si formano e faccio la media. Ripeto lo stesso processo per le altre possibili domande
Prenderò come prima domanda l'eterogeneità media migliore, cioè quella più bassa

Chiamiamo gli attributi features
Faccio variare la soglia che uso nella domanda per trovare il migliore

Un albero di decisione assegna oggetti a classi, dove un oggetto è descritto tramite un'osservazione che consiste in un vettore di valori per degli attributi fissati.
Procedimento di classificazione
- Si considera la radice dell'albero contrassegnato da una condizione che coinvolge i valori di uno o piu attributi per l'oggetto che si vuole classificare
- A seconda del valore di questa condizione si percorre una delle frecce
	- SE il nodo a cui si arriva è terminale / foglia, in tale nodo è indicata la classe dell'oggetto
	- Altrimenti il nodo riporta un'altra condizione da valutare, iterando fino al raggiungimento di una foglia

La costruzione di un albero di ricerca richiede l'individuazione di un indice di eterogeneità

ATT non necessariamente un buon comportamento degli alberi di decisione sui dati utilizzati per costruirli ci garantisce un analogo comportamento nell'indurre etichette per dati nuovi

Gli alberi di decisione si possono costruire utilizzando un qualsiasi indice che valuti l'eterogeneità
Utilizziamo la libreria sklearn supporta la scelta di un criterio con l'argomento opzionale criterion passato al costruttore DecisionTreeClassifier (valore predefinito è 'giny' ma si può optare per 'entropy')

Non può lavorare con dati qualitativi, soluzione codifica numerica con LabelEncoder

X è il dataframe
Y serie con True e False che codifica la risposta finale

es
```python
clf = tree.DecisionTreeClassifier(criterion='entropy')
clf = clf.fit(X, Y)
graphviz.Source(tree.export_graphviz(clf, out_file=None, class_names=['bad guy', 'good guy'], feature_names=features))
```

L'albero di decisione cosi utilizzato si chiama classificatore
Classificatore: Oggetto --> predizione classe a cui appartiene