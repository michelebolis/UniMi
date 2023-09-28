- L'architettura di #VonNeumann è presente negli attuali pc. Questa consiste in una Macchina di Turing in cui il nastro è unico e contiene sia dati che programma.  

- L'architettura #Harvard, invece, è una [[MdT]] in cui i nastri rappresentanti la memeria dati e programma sono separati (es Arduino)


* **CISC** (Complex Istruction Set Computing): architetture con tante instruzioni low-level di dimensione variabile che possono rischiedere diversi cicli di clock per essere completate.  CISC: Intel 8080, x86 (in realtà aveva una sezione interna che traduceva le istruzioni CISC in microistruzioni simili alle RISC)
 Vantaggi: le instruzioni possono avvicinarsi a quelle di alto livello  
 Svantaggi: la complessità computazione ne aumenta i costi di realizzazione (servono più componenti).
* **RISC** (Reduced Istruction Set Computing): architettura con poche, semplici e ottimizzate istruzioni completabili in pochi cicli di clock.  RISC: ARM, MIPS.
 Vantaggio: basso costo in silicio, grande efficienza  
 Svantaggio: difficoltà di programmazione per il basso livello. È fondamentale avere compilatori efficienti.
* **VLIW** (Very Long Instruction Word): architettura obsoleta di processori, che fu sviluppata basandosi sul concetto di parallelismo di istruzione (uso di pipeline di dati). Tutte le tecniche di miglioria apportate hannno il difetto principale di aumentare eccessivamente la complessità del microporocessore.
* **EPIC** (Explicitly Parallel Instruction Computing): tipo di architettura di microprocessori sviluppata a fine anni '90 (da Intel e HP), che aveva lo scopo di eseguire efficientemente codice parallelo senza l'ausilio di strutture HW complesse.