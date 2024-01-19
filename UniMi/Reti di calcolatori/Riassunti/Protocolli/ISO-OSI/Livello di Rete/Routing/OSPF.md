`OSPF - Open Shortest Path First`
Algoritmo che ogni nodo della rete esegue tutte le volte che riceve un update di un LS, in particolare usa l'algoritmo di Dijkstra

Vantaggi:
- Maggiore flessibilità
- Convergenza sicura

Svantaggi: rallento traffico e ho un costo computazionale

Come ragiona un nodo
Livelli di tabelle
- Tabella di `adiacenze` che popolo attraverso le ICMP: dato il nodo della rete destinazione, indica la porta del router associata
- Tabella di `routing`: dato il nodo della rete destinazione, indica l'hop da eseguire e il costo totale del cammino
- Tabella `NetID`: dato il NetID della destinazione, indica il nodo a cui mandare il pacchetto

Uso combinazione routing (guardo le 3 tabelle) e forwarding (faccio un hop). Fasi:
1. Ispeziono la NetID table per ricavare, dato il NetID destinazione, il nodo a cui inviare il pacchetto
2. Ispezione la routing table per capire come raggiungere il nodo destinazione
3. Ispezione la tabella di adiacenza per ricavare la porta del router a cui inviare il pacchetto per raggiungere il nodo destinazione

![[photo_5769355704325488902_y.jpg|400]]

[[Spanning tree broadcast]]