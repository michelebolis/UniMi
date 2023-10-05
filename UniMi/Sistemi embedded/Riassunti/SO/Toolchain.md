Sono ==strumenti per la compilazione del codice sorgente== (librerie, linker, compilatore, debugger).  
La toolchain è ==compilata per l'architettura su cui lavora==, quindi non sono intercambiabili.

* #nativa: compilata da un sistema con la medesima architettura di quella target (comune in ambienti desktop)
* #cross-toolchain: compilata da un sistema con una architettura differente produce binari per architetture differenti (comune in ambienti embedded)