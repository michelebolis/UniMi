Abbiamo un TCP Client e un TCP Server
Abbiamo inizialmente EST, EST (EST = Established) da entrambi i lati
- [[Chiusura a 4 vie - 4 way close]]
- [[Chiusura a 3 vie - 3 way close]]

Sia la chiusura a 3 che a 4 vie NON ho dati (NON ACK) da inviare

- [[Chiusura Half-Close]]

SE il client muore prima di mandare l'ACK di chiusura, il server aspetta 2 ore e poi inizia a inviare per 10 volte un KA prob con seq = X-1 ogni 75secondi (KeepAliveTimer = 75s), SE non risponde, il server chiude la connessione