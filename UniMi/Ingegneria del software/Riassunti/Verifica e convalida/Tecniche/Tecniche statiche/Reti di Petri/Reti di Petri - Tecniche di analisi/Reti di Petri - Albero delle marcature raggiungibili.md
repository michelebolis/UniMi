Fasi
1. Crea la radice corrispondente alla marcatura iniziale, etichetta il nodo come `nuovo`
2. finché esistono nodi etichettati `nuovo`, esegui i seguenti passi
	1. seleziona una marcatura M con etichetta `nuovo` e togli l'etichetta
	2. SE M è indicata ad una marcatura sul cammino dalla radice ad M, etichetta M come `duplicata` e passa ad un'altra marcatura
	3. SE nessuna transizione è abilitata in M, etichetta la marcatura come `finale`
	4. finché esistono transizioni abilitate in M, esegui i seguenti passi per ogni transizione t abilitata in M
		1. crea la marcatura M' prodotta dallo scatto di t
		2. crea un nuovo nodo corrispondente a M', aggiungi un arco da M a M' ed etichetta M' come `nuovo` 

Analisi di raggiungibilità 
Problemi: vi è la necessità di enumerare tutte le possibili marcature raggiungibili MA se la rete non è limitata, sono infiniti

Esempio
![[Pasted image 20240131094436.png|500]]

