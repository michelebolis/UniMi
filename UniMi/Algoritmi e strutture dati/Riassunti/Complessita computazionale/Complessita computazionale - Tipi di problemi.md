Problema $\pi \subseteq I \text{ x } S$
- $I=$ universo delle possibili istanze (input)
- $S=$ universo delle soluzioni
$(x, s) \in \pi$ SE E SOLO SE $s$ è una soluzione di $\pi$ su input $x$

Tipologie di problemi:
- Ricerca: data $x \in I$ trovare $s \in S$ t.c. $(x, s) \in \pi$
- Ottimizzazione: data $x \in I$ trovare $s \in S$ t.c. $(x, s) \in\pi$ che soddisfi un criterio di ottimalità fissato
- Decisione: $\pi(x)$ una funzione binaria che restituisce 1/0; con $S=\{0, 1\}$
	- $(x, 1) \in\pi$ istanze positive
	- $(x, 0) \in\pi$ istanze negative

Es 
problemi di decisione
- $I=$ grafi non orientati
Istanze $x \in I$
Questione: x è connesso?
- $I=$ grafi non orientati pesati x N
Istanze $(x, k) \in I$
Questione: esiste un albero ricoprente di x di peso $\leq k$?

Problema di ottimizzazione: dato $G=<V, E, w>$ un grafo non orientato connesso pesato trovare un albero ricoprente di $G$ di peso minimo

Ottimizzazione vs decisione
- Ottimizzazione: dato $G=<V, E>$ un grafo non orientato trovare un sottografo completo con il max numero di vertici
- Decisione: dato $G=<V, E>$ un grafo non orientato e un intero $k \in N$ stabilire SE $G$ contiene una clique di $k$ vertici
Dato un problema di decisione che impiega $T(n)$ per trovare un algoritmo per un problema di ottimizzazione posso impiegarci $T(n)*\log n$
