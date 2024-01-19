- `ARP - Address Resolution Protocol`

ARP è infatti utilizzato per `determinare l'indirizzo MAC di un host della rete LAN dato l'indirizzo IP`
Ogni host ha infatti associato un indirizzo IP e un indirizzo MAC in una ARP cache

Fasi:
1. Alla ricezione di un pacchetto IP, l'ARP legge l'IP destinazione e determina se l'indirizzo MAC sia gia presente o meno nella sua cache 
2. SE non è presente, fa un broadcast con una `ARP request` nella LAN, che contiene sia l'IP/MAC dell'host ARP che l'IP destinazione di cui si sta richiedendo l'indirizzo MAC
3. L'host di cui si sta richiedendo l'indirizzo MAC, riconoscendo il proprio IP nella ARP request, manderà un `ARP reply` contenente il proprio indirizzo MAC 
4. L'host riceve l'`ARP reply` e aggiunge una entry nella propria cache con un TTL

L'ARP nel gateway della rete è conosciuto come `proxy ARP`
SE ho piu LAN interconnesse, vi è il proxy ARP nella macchina (per forza un router perche serve che lavori a livello 3) che collega le due LAN cosicche quando riceve l'ARP request propaga la richiesta (se il SubNet ID è il suo) e risponde specificando pero il MAC address del proxy

- `RARP - Reverse Address Resolution Protocol`

E' utilizzato dagli host non appena entrano in servizio in modo che inviino in broadcast il proprio MAC cosicche lo riceva il server ARP.
Il server, riconoscendo che è un messaggio RARP, crea una RARP reply contenente la coppia MAC/IP

[[ARP-RARP - Formato]]