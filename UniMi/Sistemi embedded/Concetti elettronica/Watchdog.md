Per '**watchdog**' si intende un meccanismo che permette il ==monitoraggio grossolano di un device==. 
Tipicamente è un circuito elettronico esterno che viene opportunamente stimolato tramite segnale di un apposito GPIO.

In assenza di segnale sul GPIO viene resettato il device. 
Semantica del segnale: "sono vivo, tutto bene". 
La ratio è che un reboot risolva i problemi.

Esempio: sistema IoT che raccoglie dati ambientali da un sensore e li trasmette periodicamente ad un server remoto tramite connessione wireless. Il nodo IoT esegue ciclicamente una serie di azioni e misurazioni e, nel momento in cui termina ognuna di queste azioni, viene riavviato il Watchdog per segnalare che "va tutto bene".

Supponiamo che il Watchdog in questione abbia un contatore, a cui è assegnato un valore, e viene decrementato. Nel momento in cui dal valore massimo si arriva allo 0, significa che deve essere attivata la procedura di reset del sistema, poiché si è verificato un malfunzionamento.