1. Durante l'accessione o a seguito del reset, il bootloader controlla il pin di ricezione seriale per qualche secondo.
	1. Se riceve una sequenza di byte predefinita allora il bootloader risponde con un ACK e l'IDE invia il codice e lo scrive sulla flash.
	2. Altrimenti esegue il codice già presente sulla flash.

Direttive al precompilatore
* #"==include==: il precompilatore le sostituisce con il reale contenuto del file incluso prima di passare il tutto al compilatore
* #"==define==: il precompilatore sostituisce nel codice tutti le variabili definire con il loro reale contenuto