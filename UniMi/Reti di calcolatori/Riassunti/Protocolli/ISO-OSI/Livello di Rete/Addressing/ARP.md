ARP Address Resolution Protocol 
Risolve un indirizzo IP in un indirizzo MAC mandando un ARP request in broadcast e la macchina destinataria rispondera con una ARP reply (ma essendoci specifica l IP address, solo la macchina giusta rispondera) 
Sara conservata una tabella con un time to leave in cui vengono salvati gli IP e il MAC address

SE ho piu LAN interconnesse, vi è il Proxy ARP nella macchina (per forza un router perche serve che lavori a livello 3) che collega le due LAN cosicche quando riceve l'ARP request propaga la richiesta (se il SubNet ID è il suo) e risponde specificando pero il MAC address del proxy

RARP Reverse ARP


formato pacchetti 802.3

| Campo            |  Bytes   | Note    |
| ----------- | --- | --- |
| DA          | 6   |     |
| SA          | 6   |     |
| Type/lenght | 2   | 0806 = ARP    |

formato pacchetto ARP 

| Campo                               | bit |     |
| ----------------------------------- | ----- | --- |
| HW type                             |  16     |     |
| Protocol Type                       |    16   |     |
| ...                                 |       |     |
| Operator                            |      16 |     |
| Sender HW address | 16      |  MAC del gateway   |
| Sender IP address                   |   16    |     |
| Target HW address                   |     16  |     |
| target IP address                                    |  16     |     |
