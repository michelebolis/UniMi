Variabile $W_C$ (`Finestra di congestione`) viene aggiunta solo nella sorgente
Caso rete senza congestione
1. `Slow Start`: partendo da $W_C=1$, ogni volta che ricevo un ACK, aumento di 1 la $W_C$, risultando in un aumento veloce della finestra (Slow = cauto) fino ad una soglia, la `SST Slow Start Threshold`
2. Fase di `prevenzione della congestione`: al raggiungimento della `SST`, aumento $W_C$ di 1 (MSS) ogni $W_C$ ACK ricevuti 
3. Continuo ad aumentare $W_C$ fino a raggiungere una fase di crociera in cui non lo aumento piu 

Numero di byte che posso trasmettere è dato dal $min(W_C, W_S)$

Tipi di congestione:
- [[WC - RTO expires]] 
- [[WC - 3 ACK duplicati]]

[[Explicit Congestion Notification]]
