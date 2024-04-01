Passi
- Visito vertice $s$
- Percorro un cammino di vertici non ancora raggiunti visitandoli tutti, fermandomi su un vertice privo di vicini
- Si riparte dall'ultimo vertice sul cammino precedente che ha un vertice non raggiunto

```
ALGORITMO visitaInProfondita(grafo G=(V, E), vertice s) -> Albero
T <- albero formato solo da s
visitaRicorsiva(G, s, T)
RETURN T

PROCEDURA visitaRicorsiva(grafo G=(V, E), vertice u, albero T)
Marca u come visitato
FOR EACH (u, v) IN E DO
	IF v non è mercato come visitato THEN
		Aggiungi v e (u, v) a T
		visitaRicorsiva(G, v, T)
```