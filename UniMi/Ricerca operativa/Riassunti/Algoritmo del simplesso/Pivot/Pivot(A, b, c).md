Ogni iterazione consiste in un `cambio di base`: `una variabile in base esce dalla base` e `una variabile fuori base entra in base` 
Geometricamente è come se ci muovessimo dal un vertice a un vertice adiacente

1. `Scelgo un elemento pivot positivo posto su una colonna fuori base`
2. `Divido la riga del pivot per il pivot`, in modo che il pivot diventi 1
3. Sottraggo ad ogni riga diversa da quella del pivot, la riga del pivot moltiplicata per $a_{ic}$ cioè il coefficiente sulla riga i-esimo e sulla colonna del pivot. Nella colonna del pivot compariranno tutti 0 tranne il pivot. entra quindi in base la colonna del pivot ed esce di base la colonna corrispondente alla riga del pivot

[[Es Pivot]]
[[Pivot(A, b, c) - Interpretazioni]]

Per determinare l'elemento pivot sono necessarie una regola di scelta della colonna e una regola di scelta della riga