Nella topologia punto a punto, i nodi comunicano in modo diretto ad un solo altro nodo.
Nel topologia `broadcast` tutti i nodi sono collegati allo stesso dispositivo fisico, es [[Hub]] o bus, comunicando in broadcast

OSS nella topologia magliata/punto punto per comunicare in broadcast dovrei mandare tanti messaggi quanti sono i nodi MA tutti riceverebbero il messaggio piu di una volta

Nel broadcast, avendo garanzia che tutti nodi possano fare un check sull'indirizzo destinatario, ho la certezza che il messaggio arrivi al giusto destinatario.

Ethernet è una rete broadcast.
Per la parte fissa, inizialmente è nata come bus lineare

E' necessario gestire l'accesso mutuamente esclusivo al canale (che sia esso un centro stella hub o un bus) comune.
Una collisione si verifica quando due o piu stazioni provano a trasmettere un frame sul bus nello stesso tempo. 

ES collisione al tempo $t_2$
![[photo_5769355704325488861_y.jpg]]

Protocolli di accesso condiviso per reti broadcast
- [[Protocollo token-ring]]
- [[Protocollo Ethernet]]