Sono collezioni di dati da cui gli elementi vengono prelevati secondo un certo criterio di priorità
Ogni elemento ha una chiave, chiave piu piccola --> priorità maggiore

Operazioni:
- findMin(): restituisce l'elemento minimo della coda $O(1)$
- deleteMin(): rimuove l'elemento minimo della coda E lo restituisce $\Theta(\log n)$
- Delete(elem e): $\Theta(\log n)$
- insert(elem e, chiave d): inserisce nella coda un elemento e con associa una chiave di priorità k. Per eliminarlo lo si cambia con l'ultima foglia e poi si risistema l'albero. Costo $\Theta(\log n)$
- changeKey(elem e, chiave d): modifica la priorità dell'elemento e assegnando come nuovo valore d. Costo $\Theta(\log n)$

