Algoritmi QuickFind
- Considero alberi di altezza 1
- Gli elementi dell'insieme sono le foglie
- Il nome dell'insieme è la radice

Operazioni
- MAKESET(elemento e): $T(n)=O(1)$
- FIND(elemento e) -> nome: $T(n)=O(1)$
- UNION(nome A, nome B): $T(n)=O(n)$

Spazio $S(n)=O(n)$

QuickFind con bilanciamento sull'UNION
- MAKESET uguale
- FIND uguale
- UNION(nome A, nome B)

```
IF size(A)>=size(B) THEN
	Sposta i puntatori dalle foglie di B ad A
	Rimuovi la radice di B
ELSE
	Sposta i puntatori dalle foglie di A a B
	Rinomina la radice di B come A
	Rimuovi la vecchia radice di A
Size(A) <- size(A) + size(B)
```

Si può dimostrare che effettuando una sequenza di $n$ MAKESET e UNION e FIND il tempo totale è $O(n*lg n)$
UNION ha un costo ammortizzato di $O(\log n)$

es
![[Pasted image 20240401132219.png]]
