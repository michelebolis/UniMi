Le VLAN permettono l'aggregazione delle stazioni in gruppi omogenei, Standard IEEE 802.1Q
I frame nelle VLAN non vengono solo instradate secondo il loro MAC address ma anche secondo il proprio VLAN identifier in quanto end system di due VLAN diverse non possono comunicare.
E' uno strumento organizzativo molto utilizzato

Il campo type/length presente nell'header di Ethernet viene sostituito da un campo type settato a 8100Hex, che indica il VLAN protocol ID
I successivi 2 byte indica altre informazioni tra cui gli ultimi 12 bit rappresentano il VLAN identifier che permette l'identificazione della VLAN del mittente
I successivi 2 byte sono invece per il campo length che conterra la lunghezza del payload (campo type/length di Ethernet)

Per poterla realizzare è necessario modificare il bridge/switch in modo tale che nel processo di learning, impari anche il colore/gruppo della stazione. 
Inoltre è necessario cambiare le schede di rete delle stazioni in modo che includa anche il colore del gruppo a cui appartiene

Opinione del Rossi: se cambia volendo una VLAN, dovro aprire il mio dispositivo, cambiare la scheda di rete per tutti i device, rischia di diventare oneroso

Solitamente si prende uno switch non cambiando la scheda delle singole stazioni, lavorando solo sullo switch, taggando le porte a configuration time 
Permetto alle stazioni di generare traffico untagged e appena arriva allo switch si ha il tag