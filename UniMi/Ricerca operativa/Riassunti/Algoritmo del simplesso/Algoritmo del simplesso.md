L'algoritmo del simplesso `non da garanzia di terminare in un numero di iterazioni limitato da un polinomio` MA è molto veloce 

L'algoritmo `garantisce di terminare in un numero finito di passi`, garantendo una di queste tre situazioni
- `la soluzione corrente è ottima`
- `NON esiste una soluzione ammissibile`
- `NON esiste soluzione ottima finita`

L'algoritmo del simplesso `procede iterativamente da una soluzione di base ad una adiacente`

Data la [[Forma canonica|forma canonica]] di un problema di PL si puo rappresentare in una matrice, `tableau`.
E' una struttura dati fondamentale sulla quale opera l'algoritmo del simplesso

[[Pseudocodice algoritmo del simplesso]]