ho un timer che mi determina la Rate in base alla quale riempio il bucket di token. Qualsiasi quantità di dati la sorgente generi, dalla coda prendo il pacchetto SOLO se c è un token nel bucket
SE finisco i token, sto andando a una Rate superiore a quanto dichiarato

La coda che va in overflow eventualmente sarà quella di input