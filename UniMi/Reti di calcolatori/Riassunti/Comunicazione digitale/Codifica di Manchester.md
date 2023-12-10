La codifica di Manchester  attua l'estrazione e codifica del clock
Ogni bit è codificato come basso-alto (1) o alto-basso (0), prevedendo quindi sempre una transazione, che avviene al centro di un ogni "cella" del bit
Il segnale di clock si ottiene shiftando di mezzo bit cell dal centro

Per estrarre il clock in ricezione il livello fisico aggiunge 7+1 byte di preambolo nel messaggio, in modo che il destinatario riesca ad estrarre il clock e fare diventare il proprio come quello estratto. 
In particolare 10101010101010 e poi 011

Codificando manchester la sequenza di 10101010101010 ottengo la stessa ma shiftata di mezzo colpo di clock, dando cosi la possibilità al ricevente, in base ai fronti della sequenza, di sincronizzare il proprio clock

Quando il bit rate supera i 10Mbps NON è piu possibile utilizzare la codifica di Manchester