Open Shortest Path First
Algoritmo che ogni nodo della rete esegue tutte le volte che riceve un update di un LS, in particolare usa l'algoritmo di Dijkstra

Vantaggi:
- Maggiore flessibilità
- Convergenza sicura
Svantaggi: rallento traffico e ho un costo computazionale

Come ragiona un nodo
Livelli di tabelle
- Tabella di adiacenze che popolo attraverso le ICMP
- Tabella di routing
- Tabella NET ID

Uso combinazione routing (guardo le 3 tabelle) e forwarding (faccio un hop)

Un router è assegnato come designated router per l'AS backbone e tutti i router adiacenti.
Lo scambio di informazioni per il routing avviene SOLO tra i ruoter e il designated router