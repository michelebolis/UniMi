Nel punto a punto, i nodi parlano in modo diretto ad un solo altro link 
Nel broadcast tutti sono collegati allo stesso dispositivo fisico, es hub o bus

OSS nella topologia magliata per fare broadcast dovrei mandare tanti messaggi quanti sono i nodi MA tutti riceverebbero il messaggio piu di una volta

Avendo garanzia che tutti nodi possano fare un check sull'indirizzo destinatario, ho la certezza che il messaggio arrivi al giusto destinatario.

Ethernet è una rete broadcast.
Per la parte fissa, inizialmente è nata come bus lineare

Bus lineare: formato da un cavo coassiale, a cui si connettono i transiver di un nodo con un proprio cavo che tocca il mezzo conduttore interno 
SE A trasmette il suo segnale si propaga a dx e sx, raggiungendo tutti i nodi (secondo le regole di propagazione raggiunge tutti i nodi in momenti diversi in base alla loro distanza dal mittente)
Nativamente il messaggio è ricevuto da tutti i nodi


E' necessario gestire l'accesso mutuamente esclusivo al canale (che sia esso un centro stella hub o un bus) comune

Protocolli di accesso condiviso per reti broadcast
- [[Protocollo token-ring]]
- [[Protocollo Ethernet]]