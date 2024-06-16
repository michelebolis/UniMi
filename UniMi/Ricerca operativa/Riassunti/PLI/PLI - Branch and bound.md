Dato un problema difficile $P$, viene ricorsivamente scomposto in piu sottoproblemi $F_1, ...,F_n$ piu facili
La scomposizione/branching/ramificazione deve rispettare una `condizione per assicurare la correttezza dell'algoritmo` (non perdere la soluzioni ottime dei figli)
$$X(P) = \bigcup_{i=1}^{n}{X(F_i)}$$
La soluzione ottima di $P$ è determinata `confrontando le soluzioni ottime dei sotto problemi originati da esso`
es in caso di minimizzazione
$$z^*(P) = min_{i=1,...,n}\{z^*(F_i)\}$$
La scomposizione ricorsiva di problemi genera un'`arborescenza/decision tree/search tree` in cui la radice corrisponde al problema originale $P$ ed ogni altro nodo corrisponde ad un sotto problema
![[Pasted image 20240327134723.png|300]]

Foglie dell'albero
La procedura ricorsiva di branching `termina` quando il sotto problema corrente 
- è `inammissibile`
- è `risolto all'ottimo`
- puo essere `trascurato`

`Tutti i casi si possono rilevare risolvendo un rilassamento del sotto problema corrente`

[[PLI - Branching]]
[[PLI - Rilassamento, Corollari]]
[[PLI - Bounding]]

Strategia di visita dell'albero
Ogni volta che due o piu sotto problemi vengono generati, essi vengono appesi ad una lista di nodi aperti, cioe sotto problemi da risolvere

La politica seguita per decidere quali nodi visitare per primi è detta `search strategy`.
Il sotto problema corrente è quello che viene risolto ad un generico istante durante l'esecuzione

Criteri 
- FIFO
- LIFO
- Lista ordinata: best first search (basata sul valore del bound duale) (si utilizza un heap)