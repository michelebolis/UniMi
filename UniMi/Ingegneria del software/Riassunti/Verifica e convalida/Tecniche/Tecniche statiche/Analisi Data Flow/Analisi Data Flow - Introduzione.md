I primi utilizzi sono stati per ottimizzare i [[Compilatori - Analisi|compilatori]]
Il flusso dei dati è un'analisi dinamica MA il sottoinsieme dei controlli statici è significativo
Staticamente è possibile identificare il tipo di operazione che un comando esegue su una variabile
- Definizione (`d`): assegnamento di un valore alla variabile (o passaggio come parametro ad una funzione)
- Uso (`u`): richiesta del valore di una variabile
- Annullamento (`a`): SE al termine dell'istruzione il valore della variabile non è affidabile (es float x; non è affidabile)

Per ogni variabile è possibile ridurre una sequenza di istruzioni in una sequenza di `d`, `u`, `a`

![[Pasted image 20231211090517.png]]

[[Regole Data Flow]]
[[Sequenze Data Flow]]
[[Analisi Data Flow - File]]