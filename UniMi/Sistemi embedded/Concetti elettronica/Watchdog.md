Per '**watchdog**' si intende un meccanismo che permette il monitoraggio grossolano di un device. Tipicamente è un circuito elettronico esterno che viene opportunamente stimolato tramite segnale di un apposito GPIO.

In assenza di segnale sul GPIO viene resettato il device. Semantica del segnale: "sono vivo, tutto bene". La ratio è che un reboot risolva i problemi.