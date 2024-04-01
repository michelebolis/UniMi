DEF Algoritmo: qualsiasi schema o procedimento sistematico di calcolo (computazionale)

Algoritmo: insieme ordinato e finito di passi eseguibili e non ambigui che definiscono un procedimento che termina

- Un passo di un algoritmo (dipende dall'ambito e dall'esecutore)
- Per eseguibili intendiamo che l'esecutore possa essere in grado di fare i passi
- Non ambigui vuol dire che non debba essere lasciato all'esecutore interpretazione. Ci sono dei casi in cui l'algoritmo è progettato per far scegliere all esecutore o per avere numeri random --> algoritmi randomizzati
- Il procedimento deve terminare in un numero finito di passi. Ma per esempio ci sono device che dovrebbero restare sempre accesi es router i cui processi infatti non terminano mai

Es usare randomizzazione per calcolare l integrale: posso generare dei numeri e calcolarmi l'f(x) vedendo se il valore sta sotto o sopra rispetto a una y, calcolando la % e poi applicando la stessa % al rettangolo risultante
Es usare randomizzazione per quicksort

Algoritmi come trasformazioni input --> output
Un algoritmo $A$ possiamo vederlo come $f_a : D_I -> D_S$ con $D_I$ dominio delle istanze e $D_S$ dominio della soluzione
Gli algoritmi devono risolvere dei problemi quindi formalizziamo i problemi
Un problema $P$ sarà espresso da un'istanza $x \in D_I$ e una soluzione $f(x) \in D_S$ 

L'algoritmo A risolve il problema $P \leftrightarrow \forall x \in D_I, f_a(x)=f(x)$

Es moltiplicazione di due numeri naturali
DI = N x N istanza (x, y) appartenente a N x N
DS = N soluzione f(x, y) = xy

DEF Programma è un insieme ordinato e finito di istruzioni scritte secondo regole di uno specifico linguaggio di programmazione (non è richiesto che termini il procedimento)

Gli algoritmi li esprimiamo in pseudo codice per non preoccuparci dei dettagli dei linguaggi

Es ALGORITMO moltiplicazione (intero a, intero b) --> intero
	return $a*b$

