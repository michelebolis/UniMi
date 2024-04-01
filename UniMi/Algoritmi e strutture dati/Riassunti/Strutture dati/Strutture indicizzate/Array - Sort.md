Elaboratore gran parte del tempo li passano a ordinare dati
- Ordinamento interno: dati in memoria centrale --> accesso diretto agli elementi (tipicamente array)
- Ordinamento esterno: dati in memoria di massa --> accesso a blocchi di dati, causa lentezza periferiche

Ordinamento interno
I vettori di strutture complesse, come oggetti o record
Un particolare campo è scelto come chiave per l'ordinamento
OSS per semplicità ordiniamo array di interi

Stabilità: un algoritmo è detto stabile SE preserva l'ordine relativo tra record con la medesima chiave

Per es se ho due chiavi con lo stesso numero 15(first) 10 15(second) quando lo ordino avrò 10 15(first) 15(second)

Algoritmi di ordinamento basati su confronto tra chiavi
- Spazio: consideriamo la memoria utilizzata in aggiunta all'array da ordinare
- Tempo: in funzione della lunghezza del vettore da ordinare si calcola prima di tutto il numero di confronti tra chiavi

Le operazioni di confronto sono quelle più costose
SE ciascun confronto viene fatto in tempo costante, il numero di confronti fornisce una stima del tempo calcolato
In generale $tempoCalcolo=numeroConfronti*tempoPerConfronto$

Perche i confronti e non gli spostamenti?
Spostamenti potrebbero causare grandi spostamenti di record
In realtà potremmo vedere i record come puntatori a strutture, basterebbe scambiare il puntatore

Algoritmi elementari: tempo $\Theta(n^2)$
- Per selezione: [[SelectionSort]]
- Per inserimento: [[InsertionSort]]
- A bolle: [[BubbleSort]]

Algoritmi avanzati: tempo $\Theta(n*\log n)$
- Per fusione: [[MergeSort]]
- Veloce: [[QuickSort]] 
- Basato su heap: [[HeapSort]]

Questi algoritmi sono in loco, cioè non usa strutture aggiuntive, tranne merge e anche il quick diciamo
MA non tutti sono stabili

| Algoritmo     | Numero Confronti                                                               | Spazio                                                                                                | Note                                                        |
| ------------- | ------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| SelectionSort | $\Theta(n^2)$                                                                  | $O(n)$                                                                                                | In loco e NON stabile                                       |
| InsertionSort | $\Theta(n^2)$<br><br>Caso peggiore: array gia ordinato                         | $O(n)$                                                                                                | In loco e stabile                                           |
| Bubble        | $\Theta(n^2)$                                                                  | $O(n)$                                                                                                | In loco e stabile                                           |
| mergeSort     | $Theta(n*\log n)$                                                              | $\Theta(n)$<br>Array per il merge: $O(n)$<br>Spazio ricorsione $\Theta(\log n)$                       | NON in loco e NON stabile<br><br>Basato su divide et impera |
| quickSort     | Medio $1,39*n*\log n$<br>Peggiore $\Theta(n^2)$<br>Migliore $\Theta(n*\log n)$ | Stack della ricorsione di altezza $\Theta(n)$ nel caso peggiore<br>Nel caso migliore $\Theta(\log n)$ | In loco e NON stabile                                       |
L'ordinamento si basa sui confronti
Osserviamo che $x_i <= x_j$ ha risposta binaria
Possibili computazioni rappresentabili da un albero di decisione
Almeno una foglia per ogni permutazione $n!$ foglie
Altezza dell'albero = $\log_2 n!$

Caso peggiore percorso da radice a figlia a profondità massima
Ma quanto vale $\log_2n!$
Uso la formula di stearling: $n! = \sqrt{2\pi n}(\frac{n}{e})^n$
$$\log_2n! \approx \log_2(\sqrt{2\pi n}(\frac{n}{e})^n) = \log_2\sqrt{2\pi} + \log_2{\sqrt{n}}+\log_2(\frac{n}{e})^e$$
$$\log_2{\sqrt{2\pi}}+\frac{1}{2}\log_2n+n\log_2n-n\log_2e$$
$\Theta(n*\log n)$
Ogni algoritmo basato su confronti nel caso peggiore deve almeno avere $n*\log n$ confronti tra chiavi per riordinare n elementi

Algoritmi di ordinamento senza confronti tra chiavi
Riusciamo ad ordinare in meno di $\Theta(n*\log n)$?
Problema: ordinare n interi in $[0…b-1]$
- [[IntegerSort]]
- [[BucketSort]]
- [[RadixSort]]