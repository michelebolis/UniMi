Struttura della rete
Email client - Email server nella rete ISP Internet Server Provider - AG - Global Internet - AG - Email server - Email client

UA User Agent client si interfaccia con un altro UA sul Email server
UA prende la mail e la mette code e poi arriva al MTA Mail Transfer Agent che manderà la mail al nome@dominio utilizzando DNS per risolvere il nome simbolico del destinatario. Il trasferimento viene fatto con SMTP a livello 5 e TCP al livello 4


1. Quando un utente preme sul tasto SEND, lo UA formatta il messaggio e lo invia con MTA allo UA del server nel suo server di mail locale che ricevendo lo mail, la deposita nella coda del MTA.
2. L'MTA del server, controllando a intervalli regolari la sua coda, preleva dalla coda IN la mail. Una volta prelevato il messaggio legge il campo From e To e li scrive in MAIL FROM e RCPT TO e SE non conosce il dominio del destinatario, usa il `Resolver` per ottenere l'indirizzo IP con DNS (in particolare Type=MX). 
3. Una volta risolto con una porta X, apre una connessione TCP sulla porta 25 con il email server con HELO Mailserver-name.

Viene mandato MAIL FROM: \<email del sender>
Viene mandato RCPT TO: \<email>
Viene aggiunta la riga vuota
Data
QUIT

4. La mail arrivata all'altro server, viene messa nell'IN della Mailbox. 
5. Il destinatario userà IMAP/POP 3 per aggiornare le mail in arrivo