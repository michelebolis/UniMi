Assumiamo che l'I-frane N+1 sia corrotto e che il destinatario abbia ricevuto il frame N+2 fuori sequenza. 
Il destinatario invia al mittente un $NACK(N+1)$, causando la sospensione dell'invio di nuovi frame. 
Il destinatario scarta nuovi frame finchè non riceve l'$ACK(N+1)$.

Assumendo che $ACK(N)$ e $ACK(N+1)$ siano corrotto, il mittente alla ricezione dell'$ACK(N+2)$, assume che i primi due ACK siano stati corrotti ma non li invia nuovamente in quanto ha ricevuto ACK di un frame successivo