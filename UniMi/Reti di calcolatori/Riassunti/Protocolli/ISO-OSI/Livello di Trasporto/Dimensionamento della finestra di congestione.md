Variabile $W_C$ (Finestra di congestione) viene aggiunta solo nella sorgente
Caso rete senza congestione
- Slow Start: Ogni volta che ricevo un ACK aumento di 1 la $W_C$, risultando in un aumento veloce della finestra (Slow = cauto) fino ad una soglia, la Slow Start Threshold
- Aumento lineare: al raggiungimento della Threshold, aumento $W_C$ ogni n ACK con n = Threshold
- Continuo ad aumentare $W_C$ fino a raggiungere una fase di crociera in cui non lo aumento piu 

$NumeroDiByteChePossoTrasmettere = min(W_C, W_S)$

Problemi:
- [[RTO expires]] 
- [[3 ACK duplicati]]

3 ACK potrebbero essere molti
La sorgente, una volta rilevato di aver ricevuto i segmenti non in ordine, puo utilizzare un SACK (SelectiveACK) per specificare il segmento che ho ricevuto insieme al ACK che rappresenta invece quello che mi aspettavo


[[Explicit Congestion Notification]]
