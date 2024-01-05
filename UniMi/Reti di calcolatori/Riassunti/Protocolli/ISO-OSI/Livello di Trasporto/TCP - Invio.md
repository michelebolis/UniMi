Assumiamo che non ci siano errori nella connessione e che la dimensione dei messaggi al livello applicazione sia maggiore della dimensione del segmento

Sorgente con messaggio da scrivere di 600byte
Sorgente con SEQ = X e destinazione con SEQ = Y
MSS = 500byte

L'applicazione del sorgente scrive il messaggio nel buffer della socket
E' necessario fare due segmenti: uno da 500 e uno da 100

1. Mando il primo segmento con SEQ = X, che conservo nel buffer TCP del mittente con tutti gli altri segmenti
2. Il ricevente controlla che sia il SEQ che si aspettava e lo mette nel buffer ricezione del TCP. Coi suoi tempi i segmenti vengono inviati dal buffer TCP a quello del receiver
3. Il ricevente manda un segmento con ACK=1, ACK = X + 500
4. Il mittente, ricevuto il segmento di ACK, cancello nel buffer TCP il primo segmento e mando il secondo segmento con SEQ=X+500
5. Ricevente ripete passo 2 mandando un ACK=X+600
6. Alla ricezione dell'ACK, tutti i segmenti sono stati inviati

Ottimizzazioni:
- [[Cumulative ACK]]
- [[TCP - Invio continuo]]

[[TCP - Controllo dell'errore]]
