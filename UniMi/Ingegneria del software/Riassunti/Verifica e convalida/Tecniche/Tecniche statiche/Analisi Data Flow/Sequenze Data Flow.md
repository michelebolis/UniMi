`P(p, a)` indica la sequenza ottenuta per la variabile `a` eseguendo il cammino.
Per rappresentare `P` in caso di cammini contenenti cicli e decisioni si possono usare espressioni regolari in cui:
- `|` indica che i simboli a destra e a sinistra si escludono a vicenda
- `*` indica che il simbolo può essere ripetuto da `0` a `n` volte

ATT le espressioni regolari rappresentano tutti i cammini MA NON solo tutti i cammini del programma
Si dimostra `impossibile scrivere un algoritmo che dato un programma P riesca a generare un'espressione regolare che rappresenti tutti e soli i suoi cammini possibili`.
L'analisi Data Flow tramite espressioni regolari, genera un astrazione pessimistica

es
![[Pasted image 20231211092708.png|200]]

$P([1 ->], a)$
$a_2,\text{ }d_5,\text{ }u_7(u_8\text{ }(u_9d_9 | u_{11}))^*\text{ }u_{12},\text{ }a_{13}$