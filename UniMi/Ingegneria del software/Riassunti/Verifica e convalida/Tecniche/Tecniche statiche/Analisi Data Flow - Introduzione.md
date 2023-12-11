I primi utilizzi sono stati per ottimizzare i [[Compilatori - Analisi|compilatori]]
Il flusso dei dati è un'analisi dinamica MA il sottoinsieme dei controlli statici è significativo
Staticamente è possibile identificare il tipo di operazione che un comando esegue su una variabile
- Definizione: assegnamento di un valore alla variabile
- Uso: richiesta del valore di una variabile
- Annullamento: SE al termine dell'istruzione il valore della variabile non è affidabile (es float x; non è affidabile)

Per ogni variabile è possibile ridurre una sequenza di istruzioni in una sequenza di 
- d (definizioni)
- u (usi)
- a (annullamenti)

![[Pasted image 20231211090517.png]]

[[Regole Data Flow]]
[[Sequenze Data Flow]]
[[Analisi Data Flow - File]]