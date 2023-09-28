 Un HW #interrupt non è altro che un modo che una periferica di qualsiasi tipo ha per segnalare al processore di eseguire azioni spefifiche fermandosi, salvano ciò che stava facendo (tipicamente nello stack) e, infine, riprenderlo una volta completata l'azione richiesta inizialmente dalla periferica.
 
 si può adibire un pin a segnale di interrupt associato ad una funzione. Nel caso in cui si verifichi l'evento definito su quel pin (es arduino: LOW, HIGH, CHANGE, RISING, FALLING) viene stoppata l'esecuzione del loop ed eseguita la funzione designata.

 ```c
 attachInterrupt(digitalPinToInterrupt(pin), ISR, mode) //ISR puntatore alla funzione di risposta
 ```