E' un particolare metodo di suddivisione in classi di equivalenza usabile a diversi livelli di granularità (Test di unità, di integrazione e di sistema)

Passi:
1. Analizzare le specifiche: identificare le unita funzionali individuali che possono essere verificate singolarmente e, per ogni unita, identificare le caratteristiche (categorie) dei parametri e dell'ambiente
2. Scegliere dei valori per le categorie
3. Determinare eventuali vincoli tra le scelte per eliminare combinazioni meno significative
	- proprietà (es NotEmpty)
	- Error
4. Scrivere test e documentazione: è possibile stimare il numero di casi di test e generare specifiche in modo automatico
	- Numero e distribuzione dei vincoli possono essere determinati iterativamente stimando i casi di test
		- generando le specifiche a partire da scelte e vincoli quando la stima dei casi di test è ragionevole
		- valutando i test generati ed introducendo nuovi vincoli SE vi sono forti ridondanze

Criticità
- individuazione dei casi significativi
- una volta generati i casi di test serve un oracolo che fornisca la risposta giusta, non ottenendo quindi un'attività completamente automatizzabile