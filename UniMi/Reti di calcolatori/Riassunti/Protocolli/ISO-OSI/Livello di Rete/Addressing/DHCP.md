Il client fa una richiesta, DHCP Discover. Campi: IP sorgente (0.0.0.0), IP destinazione del DHCP server (255.255.255.255), TID transaction ID (generato dal client)
Il server associa MAC address - TID, mandando una DHCP Offer che manda al client. Campo: IP Sorgente (IP Server), ..., TID
Per verificare che IP address non sia gia in utilizzo dagli altri, il server fa un ping con l IP address che sta offrendo
Il client prende atto dell offerta, potenzialmente piu di una (se ci sono piu server).
Il client produce una DHCP request. Campi: IP Sorgente (0.0.0.0), IP Destinazione (IP Server sempre in broadcast), TID
Da quel momento in poi al client è assegnato quell IP, il server manda quindi un DHCP ACK
Da quando ricevo ACK il client diventa indirizzabile MA prima il client fa check attravero un ARP request (non dovrebbe rispondermi nessuno)

DHCP funziona a 4 vie (Discover-Offer-Request-ACK) perche i server sono piu di uno

Vengono inseriti controlli per la discover e la request, ripetendo nel caso la ritrasmissione per al massimo k tentativi
