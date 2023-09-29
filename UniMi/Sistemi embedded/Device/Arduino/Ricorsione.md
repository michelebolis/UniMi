L'uso della ricorsione permette spesso di scrivere codice più leggibile e semplice, ma il record di attivazione delle chiamate di funzione occupa spazio nello stack.  

L'ambito dei sistemi embedded è costellato da architetture con poca memoria ram pertanto le ==chiamate ricorsive potrebbero portare ad uno stack overflow== potenzialmente non segnalato, portando effetti poco prevedibili.