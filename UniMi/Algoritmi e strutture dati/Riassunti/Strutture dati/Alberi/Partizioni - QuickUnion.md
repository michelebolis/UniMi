Algoritmi QuickUnion
- Considero alberi di VARIE altezze
- Gli elementi dell'insieme sono i nodi
- L'elemento che da il nome all'insieme è la radice

Albero peggiore: altezza di $n-1$
Operazioni
- MAKESET(elemento e): $T(n)=O(1)$
- UNION(nome A, nome B): $T(n)=O(1)$
- FIND(elemento e) -> nome: $T(n)=O(n)$, Numero passi=altezza

es
![[Pasted image 20240401132334.png]]

UNION bilanciato: attacchiamo la radice dell'albero piu basso sotto quella dell'albero piu alto
Consideriamo le altezze degli alberi come rank
Operazioni:
- MAKESET uguale
- FIND uguale
- UNION
```
UNION(nome A, nome B)
IF rank(A)>rank(B) THEN
	Rendi la radice di B figlia di quella di A
ELSE IF rank(A)<rank(B) THEN
	Rendi la radice di A figlia di quella di B
	Scambia i contenuti dei nodi A e B
ELSE
	Rendi la radice di B figlia di quella di A
```
$T(n)=O(1)$

Lemma: ogni albero QuickUnion costruito effettuando operazioni di UNION bilanciate contiene almeno $2^{rank(X)}$ nodi con $X$ la radice
$Numero Nodi\geq 2^{rank(X)}$

DIM $k=NumeroOperazioni$ UNION utilizzate per ottenere l'albero con radice $X$
Base $k=0$, 0 UNION, $rank(X)=0$, $1>=1$ VERO
Passo k>0, …

Corollario $n$ nodi -> $altezza \leq \log 2 n$ -> FIND costa tempo $O(\log n)$

QuickUnion bilanciata con compressione di cammino
Si puo dimostrare che effettuando una sequenza di n MAKESET e O(n) UNION e FIND il tempo totale è $O(n*\log n)$
QUINDI il costo ammortizzato di FIND è $O(\log n)$  