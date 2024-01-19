Alla destinazione arrivano i segmenti MA fuori ordine. 
C'è una `congestione ma non è una situazione grave` in quanto la destinazione resta raggiungibile

Data $W_C = k$ appena ricevo 3 ACK duplicati, dimezzo la finestra ($W_C = k/2$) e riprendo ad aumentare la finestra in modo lineare cioè con la fase di prevenzione della congestione, ottenendo cosi un `fast recovery`

Tuttavia 3 ACK potrebbero essere molti: SACK permitted option
