Per identificare le caratteristiche che rendono utile un caso di test o ragiono sulle caratteristiche delle specifiche o del codice

Ad ogni criterio è possibile associare una metrica che ne misuri la copertura e che ci permetta di:
- decidere quando smettere
- decidere quale altro caso di test è opportuno aggiungere
- confrontare le `boltà` di Test diversi

Un caso di test per poter portare a evidenziare un malfunzionamento causato da un'anomalia, è necessario 
- eseguire il comando che contiene l'anomalia
- l'esecuzione del comando contenente l anomalia deve portare il sistema in uno stato scorretta
- lo stato scorretto deve propagarsi fino all'uscita del codice in esame in modo da produrre un output diverso da quello atteso