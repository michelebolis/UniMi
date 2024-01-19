$Type = 0x5$

Vantaggio: risparmio tempo 

| Campo | Descrizione |
| ---- | ---- |
| Padding length |  |
| Reserved bit |  |
| Promised Stream ID | oltre ai frame header e data, restituisco anche un frame push promise in cui è contenuto l'`ID dello stream su cui il server mandera i dati` (DIVERSO da quello dell header: creato dal server) |
| Header Block Fragment |  es Content-Type: img |
| Padding |  |


