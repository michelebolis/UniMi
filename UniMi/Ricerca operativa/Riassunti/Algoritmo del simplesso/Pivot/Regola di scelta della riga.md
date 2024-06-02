Scelta la variabile che entra in base, è necessario scegliere la `variabile uscente dalla base`. Tale scelta deve garantire l'ammissibilità.
Data la variabile entrante $x_j$, cioe lo spigolo del poliedro lungo il quale la soluzione cambia, l'unica possibilita corretta è
- `muoversi verso l'interno del poliedro`
	- considerare solo candidati pivot $a_{ij}$ positivi
- `fermarsi appena si incontra una soluzione di base`
	- tra le righe $i$ ad essi corrispondenti, scegliere quella che rende minimo il rapporto tra il termine noto $b_i$ e il candidato pivot $a_{ij}$

Nel caso di parità di rapporto minimo, la `regola di Bland` impone di scegliere la riga di indice minimo (garanzia di assenza di cicli negativi)

[[Regola di scelta della riga - Esempio]]