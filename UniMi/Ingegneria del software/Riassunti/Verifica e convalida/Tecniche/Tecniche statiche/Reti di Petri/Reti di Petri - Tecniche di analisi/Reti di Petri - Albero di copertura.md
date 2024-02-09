[[Rete di Petri - Copribilità]]
Fasi:
1. Crea la radice corrispondente alla marcatura iniziale, etichetta il nodo come `nuovo`
2. finché esistono nodi etichettati come `nuovo`, esegui:
	1. seleziona una marcatura $M$ con etichetta `nuovo` e togli l'etichetta
	2. SE $M$ è identica ad una marcatura sul cammino dalla radice ad $M$, etichetta $M$ come `duplicata` e passa ad un'altra marcatura
	3. SE nessuna transizione è abilitata in $M$, etichetta la marcatura come `finale`
	4. finché esistono transizioni abilitate in $M$, esegui i seguenti passi per ogni transizione $t$ abilitata in $M$:
		1. crea la marcatura $M'$ prodotta dalla scatto di $t$
		2. SE sul cammino della radice a $M$, esiste una marcatura $M''$ coperta da $M'$, modifica $M'$ scrivendo $w$ in tutte le posizioni corrispondenti a `coperture proprie`
		3. crea un nodo corrispondente a $M'$, aggiungi un arco da $M$ a $M'$ ed etichetta M' come `nuovo`

Analisi di copribilità: `PERDO la capacita dei numeri che puo rappresentare` ($\omega$ = numero grande a piacere)
1. una rete di Petri è `limitata` SE $w$ non compare in nessun nodo dell'albero di copertura
2. una rete di Petri è `binaria` SE nell'albero di copertura compaiono SOLO 0 e 1
3. una transazione è `morta` (0-live) SE non appare come etichetta di un arco dell'albero di copertura
4. `Raggiungibilità` di una marcatura $M$
	1. `condizione necessaria` affinché una marcatura $M$ sia raggiungibile è l'esistenza di un nodo etichettato con una marcatura che copre M (NON è sufficiente in quanto non so quanto vale  $\omega$)
	2. `condizione sufficiente`: se è presente come nodo nell'albero
5. `non è possibile decidere SE una rete è viva`

Esempio
![[Pasted image 20240131095820.png|500]]

Esempio di rete non viva
![[Pasted image 20240131101140.png|500]]

