1. UA vuole mandare una mail. Contatta lo UA server, il cui IP è noto. 
2. La parte client del MTA preleva dalla coda in cui c è la mail. Legge from, to e Cc e, SE non conosce il dominio, usa il resolver per ottenere l indirizzo IP con DNS (in partizolare MX). 
3. Una volta risolto con una porta X apro una connessione TCP con l altro email server con HELO Mailserver-name.
Viene mandato MAIL FROM: \<email del sender>
Viene mandato RCPT TO: \<email>
Vengono aggiunti la riga vuota
Data
QUIT
4. La mail arrivata all'altro server, viene messa nell'IN Mailbox. 
5. Periodicamente l'UA client chiede se ci sono nuove mail all'UA del server e dato che c è, viene inviata al client