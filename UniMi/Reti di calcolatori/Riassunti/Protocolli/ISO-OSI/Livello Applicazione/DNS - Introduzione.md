DNS Domain Name System
Per contattare il server di una pagina web potrei utilizzare il suo IP MA è ovviamente piu semplice utilizzare il suo nome simbolico
DNS traduce un nome in un indirizzo IP
Un nome DNS è identificato da un fully qualified domain name
1. Per essere human readable è rappresentata in dot notation es www.di.unimi.it. (ATT a livello di standard c è un `.` finale ma in realtà è messo automaticamente)
2. Dal punto di vista della macchina è rappresentato come una stringa di byte, mettendo il numero di byte di ogni label es 3www2di5unimi2it0

Utilizzi:
- modo semplice per indirizzare un host a un server nella rete
- disaccoppiare nome-server per il load balancing: smistare le varie richieste sui vari server in base alla posizione geografica (o in round roubin per bilanciare le richieste per il sito)

[[DNS - Schema]]
[[DNS - Formato]]
[[DNS - Risoluzione]]