$P$ problema
$I$ istanza di $P$

SE $I$ è piccola risolvi $P$ su $I$ direttamente
ALTRIMENTI
- Dividi $I$ in istanze di lunghezza minore della lunghezza di $I$
- Risolvi queste istanze separatamente
- Ricava la soluzione di $I$ combinando opportunatamente le soluzioni ottenute

```
ALGORITMO risolviP(istanza I) -> soluzione
IF |I| <= C THEN
	Risolvi P su I direttamente
	RETURN soluzione trovata
ELSE
	Dividi I in m istanze ridotte I1, …, Im con |Ij| < |I| per j=1, …, m
	Sol1 <- risolviP(I1)
	…
	Solm <- risolviP(Im)
	RETURN combina(sol1, … solm)
```

OSS non posso avere troppe istanze piccole che si ripetono
OSS Spazio viene riutilizzato

[[Teorema di ricorrenza - Master theorem]]

es Prodotto tra matrici: Algoritmo di Strassen
Queste 7 matrici le calcolo con somme e prodotti ma faro solo 7 prodotti $n/2*n/2$ e 24 somme $(14+10)$ di matrici $n/2*n/2$

$T(n) = \begin{cases} 1 \text{ SE } n=1 \\ 7*T(\frac{n}{2}) + 24*(n)^2 ALTRIMENTI \end{cases}$
$T(n)=Θ(n^{\log_2 7})=Θ(n^{2,81})$

Il miglior upper bound per ora è $\Theta(n^{2,3})$
![[Pasted image 20240329110652.png]]