Link State Routing
1. Costruzione adiacenza: le tabelle di adiacenza vengono costruite nello stesso modo del DV 

2. Diffusione LS: una volta misurato il costo delle adiacenze, questa informazione non viene propagata ai nodi adiacenti, MA a tutti i nodi della rete

Questo viene fatto con il Floodind: evoluzione del broadcast che permette di propagare in un unica direzione 
Flooding viene implementato in modo che i nodi che ricevono le info di un nodo A vengono inviate in tutti i link di uscita tranne quello in cui l ho ricevuto
Ogni nodo appena riceve un LS da un nodo adiacente, manda un segnale di ACK. Questo cerca di garantire la consistenza. SE non ricevo l ACK, viene ritrasmesso il LS (ridondanza locale) ma non viene rinviato all infinito in quanto sappiamo che nelle altre direzioni verra ripropagato (ridondanza temporale)
Creo inevitabilmente dell overhead, della ridondanza di alcune info

SE ho N nodi, ho N^2 messaggi che girano

LS composto da: Sorgente, Sequence, TimeToLive, NumeroHop, 
Sequence: assegnato dalla sorgente che permettono di evitare le coppie di LS gia ricevuti

Inondando la rete di traffico di controllo TUTTI conoscono esattamente la topologia della rete
Questo ci permette di superare il problema dei DV, count to infinity

Per ogni link ho un costo bidirezionale

[[OSPF]]