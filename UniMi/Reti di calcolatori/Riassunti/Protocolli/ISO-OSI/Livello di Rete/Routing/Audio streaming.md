La digitalizzazione di un segnale analogico passa da campionamenti. Decido una frequenza di osservazione e ad ogni bit campione il valore di tensione, producendo un byte 
Piu è la frequenza di campionamento maggiore è la qualità.

8000 campioni al secondo (uno ogni 125microsecondi) per garantire...
Dato che ogni campione produce un byte, al secondo produco 64KB (minimo di banda per avere una qualità minima). Alternativa 16000 campioni al secondi quindi 128KB
PCM Pulse Code Modulation
Anche in ricezione dovro avere la stessa frequenza di arrivo dei messaggi, quindi uno ogni 125microsecondi (CBR Constant Bit Rate in ricezione)

Anche perche audio e video hanno un Jitter sensibile
Per garantire questo requisito su Internet, viene delegato al SW: Buffer di playout, permette di bufferizzare e risolvere la scarsa qualità della rete (dimensionamento in base alla qualità della rete)