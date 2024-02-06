Costruiamo un albero di raggiungibilità temporale in cui gli stati distinguibili solo dai timestamp vengono condensati in stati simbolici conservando la molteplicità nei posti e le relazioni tra i timestamp

Fasi algoritmo:
1. `Inizializzazione`: si trasforma la marcatura iniziale in uno stato simbolico. introducendo una serie di vincoli per descrivere le precondizioni. Tale stato diventa un nodo, la radice dell'albero, e aggiunto alla lista dei nodi da esaminare
2. `Scelta del prossimo nodo`: si seleziona il prossimo nodo da esaminare
3. [[Reti di Petri Temporizzate - Identificazione delle abilitazioni]]: in base allo stato simbolico rappresentato dal nodo, individuo le transizioni abilitate
4. [[Reti di Petri - Aggiornamento di marcatura e vincoli]]: ciascuna transizione abilitata viene fatta scattare generando un nuovo stato simbolico, un nuovo nodo dell'albero che viene aggiunto alla lista dei nodi da esaminare
5. Ritorno a 2

Esempio
![[Pasted image 20240131151610.png|600]]
