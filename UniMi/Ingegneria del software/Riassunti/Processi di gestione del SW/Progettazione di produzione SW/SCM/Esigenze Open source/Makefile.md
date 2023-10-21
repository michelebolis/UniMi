Un _Makefile_ è un file di testo che contiene le istruzioni per il programma make su come compilare e linkare i file sorgente di un progetto. Ogni riga del Makefile definisce un obiettivo o una dipendenza, insieme ai comandi che devono essere eseguiti per raggiungerlo. 

L’utilizzo del Makefile permette di automatizzare la compilazione e il linkaggio dei file sorgente, semplificando il processo di sviluppo di un progetto. 
Sono stati creati dei tool (`automake`, `autoconf`, `imake`, …) che _generano_ `Makefile` ad-hoc per l’ambiente attuale.

Il _mantra_:
```
$ ./configure 
$ make all 
$ sudo make install
```
era largamente utilizzato per generare un Makefile ad-hoc per l’ambiente attuale e installare il software sulla macchina in modo automatico. `automake`, `autoconf`, e `imake` sono strumenti che aiutano a questo scopo, generando Makefile che possono essere utilizzati per compilare e installare il software in modo automatico.