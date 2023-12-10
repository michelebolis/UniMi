La differenza con il bridge è che NON c'è CSMA/CD ma c'è un cavo dedicato dal nodo allo switch, quindi non ci saranno mai collisioni
Sono quindi grandi accumulatori anche a grande velocita in quanto non ci sono vincoli di distanza

Il processo nello switch legge l'header per ottenere il MAC address e trasmettere il frame alla coda di uscita corretta.
Anche lo switch ha un processo di apprendimento simile al bridge.

Spesso vengono collegati sia ai router che ad altri switch.
Connessione switch to switch viene chiamato `trank`, in questo caso passano frame di qualsiasi colore (VLAN) e sarà lo switch destinatario a gestirlo

Essendoci compatibilità con le frame posso sostituire in qualsiasi momento un bridge con uno switch
In realta il CS (del CSMA/CD) verra sempre fatto ma non ci saranno mai collisioni
Viene anche mantenuto la dimensione minima del frame anche se non serve

In realta sto aggiungendo complessita nello switch che dovra gestire molte linee a grandi velocita
