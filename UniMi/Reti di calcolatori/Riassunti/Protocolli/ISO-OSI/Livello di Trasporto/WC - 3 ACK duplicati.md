Alla destinazione arrivano i segmenti MA fuori ordine. 
C'è una congestione ma non è una situazione grave

Data $W_C = k$ appena ricevo 3 ACK duplicati, dimezzo la finestra ($W_C = k/2$) e riprendo ad aumentare la finestra in modo lineare

3 ACK potrebbero essere molti
La sorgente, una volta rilevato di aver ricevuto i segmenti non in ordine, puo utilizzare un SACK (SelectiveACK) per specificare il segmento che ho ricevuto insieme al ACK che rappresenta invece quello che mi aspettavo