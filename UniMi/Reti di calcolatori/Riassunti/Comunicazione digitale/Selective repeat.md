Ci sono $k$ buffer in $T_x$ e $k$ buffer in $R_x$
Avendo $k$ buffer, conservo i frame corretti anche se non in ordine chiedendo poi `selettivamente` al trasmettitore di inviarmi nuovamente il frame specifico

Assumiamo che l'I-frame N+1 sia corrotto e che il destinatario abbia mandato un ACK per il frame N. 
Quando il destinatario riceve il frame N+2, grazie a $V(R)$ riconosce che manca il frame N+1, inviando quindi un $NACK(N+1)$, bloccando l'invio di nuovi ACK.
Il mittente quindi invia nuovamente N+1, sospendendo la trasmissione di nuovi frame e settando un timer per la ricezione dell'ACK(N+1).
Una volta ricevuto il frame N+1, il destinatario riprende a inviare ACK MA poi invierà un ACK superiore a N+1 in quanto nella sua lista di ricezione aveva già ricevuto dei frame corretti

Assumendo che l'ACK-N sia corrotto, il mittente ritrasmette il frame N ma il ricevente, grazie a V(R), lo identifica come un duplicato, scartandolo e inviando ACK-N