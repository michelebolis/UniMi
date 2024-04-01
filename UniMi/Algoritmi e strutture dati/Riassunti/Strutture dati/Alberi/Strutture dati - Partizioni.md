Dato un insieme $A$
Le partizioni $a_1, …, a_k$ sono sottoinsiemi di $A$ t.c.
- $a_i \neq \emptyset$ con $i=1,…,k$
- $a_i \cap a_j = \emptyset$ con $i\neq j$
- $a_1 \cup … \cup a_k = A$

$S$: collezione di elementi tra loro distinti
- Organizzazione iniziale: $n$ insiemi disgiunti
- Ogni insieme ha un nome: nome iniziale $\{i\} -> i$

Problema UNION-FIND: rappresentare una collezione di insiemi disgiunti con le operazioni
- UNION(A, B): unisce gli insiemi A e B in un unico insieme di nome A
- FIND(x): restituisce il nome dell'insieme che contiene l'elemento X
- MAKESET(x): crea un insieme {x} di nome x

es
![[Pasted image 20240401131935.png]]

Ci sono diverse soluzioni sia elementari che evolute
In tutte le soluzioni presentate:
- OGNI insieme è rappresentato da un albero con radice in cui
	- Nodi= elementi dell'insieme
	- Radice= nome dell'insieme
	- Puntatori verso l'alto
- La partizione è una foresta di alberi

[[Partizioni - QuickFind]]
[[Partizioni - QuickUnion]]

| L                                                 | MAKESET | UNION            | FIND             |
| ------------------------------------------------- | ------- | ---------------- | ---------------- |
| QuickFind                                         | $O(1)$  | $O(n)$           | $O(1)$           |
| QuickFind bilanciato                              | $O(1)$  | $O(\log n)$ amm. | $O(1)$           |
| QuickUnion                                        | $O(1)$  | $O(1)$           | $O(n)$           |
| QuickUnion bilanciato                             | $O(1)$  | $O(1)$           | $O(\log n)$      |
| QuickUnion bilanciato<br>con compressione cammino | $O(1)$  | $O(1)$           | $O(\log n)$ amm. |
