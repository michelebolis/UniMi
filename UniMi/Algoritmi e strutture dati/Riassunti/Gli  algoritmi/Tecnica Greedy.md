Dato $P$ problema di ottimizzazione
- $C$ insieme di candidati
- Trovare $S^* \subseteq C$ ottima

Fasi
- A partire dall'insieme vuoto in una sequenza di passi si costruisce una soluzione ammissibile $S$
- Ad ogni passo si espande una soluzione parziale gia ottenuta
- L'algoritmo termina quando NON è piu possibile espandere la soluzione parziale

Espansione:
- Soluzione ammissibile: soluzione parziale soddisfa i vincoli del problema
- Scelta dell'ottimo locale: tra i candidati disponibili si sceglie quelle che al momento appare migliore
- Scelta irrevocabile: le scelte effettuate non vengono piu discusse

```
ALGORITMO greedy(insieme C) -> soluzione
	S <- vuoto
	WHILE C != vuoto DO
		X <- seleziona un elemento da C, scelgo il migliore
		C <- C - {X}
		IF S U {x} è ammissibile THEN S <- S U {X}
	RETURN S
```

[[Tecnica Greedy - Es]]