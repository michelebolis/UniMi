 si può adibire un pin a segnale di [[interrupt]] associato ad una funzione. Nel caso in cui si verifichi l'evento definito su quel pin (es arduino: LOW, HIGH, CHANGE, RISING, FALLING) viene stoppata l'esecuzione del loop ed eseguita la funzione designata.

 ```c
 attachInterrupt(digitalPinToInterrupt(pin), ISR, mode)
 ```

 Si possono anche definire sezioni critiche iniziando con la disabilitazione degli interrupt con noInterrupts() e la riabilitazione alla fine interrupts()