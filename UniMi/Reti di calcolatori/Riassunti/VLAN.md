A livello 2 VLAN Virtual LAN
Aggregazione delle stazioni in gruppi omogenei
Due stazioni di due gruppi diversi non possono comunicare
E' uno strumento organizzativo molto utilizzato

Per poterla realizzare è necessario modificare il bridge in modo tale che nel processo di learning, impari anche il gruppo della stazione. 
Inoltre è necessario cambiare le schede di rete delle stazioni in modo che includa anche il colore del gruppo a cui appartiene



Standard IEEE 802.1Q
Viene usato davvero il colore come discriminante tra i gruppi

il frame del VLAN utilizza il campo gia esistente lunghezza che in realta dal protocollo è previsto essere anche type
Il campo type per le frame 802.3 è 8100 in esadecimale, caratteristica di essere superiori a 1500
Altrimenti si sa che si sta lavorando con la VLAN, aggiungendo dopo 2 byte per il colore 

Opinione del Rossi: se cambia volendo una VLAN, dovro aprire il mio dispositivo, cambiare la scheda di rete per tutti i device, rischia di diventare oneroso

Solitamente si prende uno switch non cambiando la scheda delle singole stazioni, lavorando solo sullo switch, taggando le porte a configuration time 
Permetto alle stazioni di generare traffico untagged e appena arriva allo switch si ha il tag