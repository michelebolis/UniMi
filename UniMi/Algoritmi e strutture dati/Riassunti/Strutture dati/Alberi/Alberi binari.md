Ad ogni nodo possono essere associati due successori detti figlio sinistro e destro
- Radice: nodo in cima
- Sottoalbero di sinistra
- Sottoalbero di destra

OSS I sottoalberi possono essere visti come alberi
- Nodo padre
- Nodo figlio
- Un arco collega padre-figlio
- Foglie: nodi che non hanno figli
- Nodi interni: nodi con figli
//Fratello

Profondita/livello di un nodo è il numero di archi attraversati per raggiungere il nodo dalla radice
- Profondita radice = 0
- Profondita padre = $k$ --> profondita figlio = $k+1$
Altezza dell'albero: massima profondita dei nodi

Implementazione
- Puntatore da padre a figlio
- Dati: vari campi
- 2 puntatori
	- SX per accedere al sottoalbero sinistro
	- DX per accedere al sottoalbero destro

[[Alberi binari - Visita]]
