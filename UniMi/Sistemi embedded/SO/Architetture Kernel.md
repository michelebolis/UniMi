* #monolitica: il nucleo comprende driver, strutture di multiplexing dell'hw e servizio per la gestione dei processi e della comunicazione (es. linux, freeBSD)
* #microkernel:  kernel con il ==minor codice possibile eseguito in modalità supervisore==. Gli altri componenti vengono estratti in ==moduli== (es driver) comunicano con il nucleo tramite componenti software detti "server".
  * Vantaggi: sicurezze e robustezza.
  * Svantaggi: complessità di sviluppo e rigidità comportamenteale compessiva (es freeRTOS)
* #ibridi (es kernel di mecOS)