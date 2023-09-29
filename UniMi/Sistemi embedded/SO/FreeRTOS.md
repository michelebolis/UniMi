**FreeRTOS (Free Real Time Operating System)** è un sistema operativo semplice e veloce che ha lo scopo di offrire prestazioni real-time.

 Non comprende driver nè API complesse ma solo il necessario per la gestrione di thread, task, mutex, semafori e timer.

 Un prodotto finale FreeRTOS unisce il codice sorgente dei sistema a  quello per il supporto dell MCU relativa e al codice dell'applicazione.
 
 I task sono dei programmi all'interno del programma principali (ricordano i processi). Effettivamente sono funzioni conteneti un loop infinito nel quale sono presenti le istruzioni di funzionamento.  
 Può essere eseguito un solo task alla volta. Possono avere stati diversi come:

* Running: in esecuzione
* Ready: eseguibile da un momento all'altro
* Suspended: esplicitamente fermato e in attesa di esplicita riattivazioni
* Blocked: fermato e in attesa di un evento