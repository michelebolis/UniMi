`Alcuni tratti biometrici non posseggono le 7 caratteristiche` necessarie ma possono essere usate in aggiunta per l'identificazione di un utente. 

Alcuni tratti si soft biometrics ( non utilizzabili per identificare o verificare l'identità di individuo da soli) possono essere utilizzati assieme ai tratti biometrici :

Alcuni esempi di tratti :
- Genere
- Sesso
- Peso
- Altezza
- Colore della pelle
- Colore degli occhi

`L'integrazione corretta di un sistema di soft-biometrics è a valle del modulo di matching primario`.
Il modulo di matching primario ritornerà una probabilità che la feature x appartiene all'utente w del database (sarà il match score più alto). P(W|x).
Dobbiamo quindi `progettare il post processing module`:
Sceglieremo una `funzione che rappresenti al meglio i valori dati dalla formula di bayes` per tutti gli utenti ovvero P(W|x,y) con y tratto si soft biometrics.

I sistemi innovativi "multiple immages" o i 2.5d faces sono di fatto sei sistemi multi biometrici per il volto.
Il sistema iride + retina implementa due delle più accurate e resistenti agli attacchi tecnologie presenti sul mercato. Ad oggi tutta via è possibile falsificare allo stesso tempo i due tratti superando i test di liveness disponibili su questi sitemi.