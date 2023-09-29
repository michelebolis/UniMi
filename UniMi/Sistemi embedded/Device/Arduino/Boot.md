 Durante l'accessione o a seguito del reset, il bootloader controlla il pin di ricezione seriale per qualche secondo.
 Se riceve una sequanza di byte predefinita allora il bootloader risponde con un ACK e l'IDE invia il codice e lo scrive sulla flash.
 Altrimenti esegue il codice già presente sulla flash.

direttive al precompilatore
* #"include: il precompilatore le sostituisce con il reale contenduto del file incluso prima di passare il tutto al compilatore
* #"define: il precompilarore sostituisce nel codice tutti le variabili definire con il loro reale contenuto