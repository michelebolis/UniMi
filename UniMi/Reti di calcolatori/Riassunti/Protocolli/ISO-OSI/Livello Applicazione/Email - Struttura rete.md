Email client - Email server nella rete ISP Internet Server Provider - AG - Global Internet - AG - Email server - Email client

MS locale: è nel file system
MS server mail: è nei dischi del server

UA User Agent client si interfaccia con un altro UA sul Email server
UA prende la mail e la mette code e poi arriva al MTA Mail Transfer Agent che mandera la mail al nome@dominio utilizzando DNS per risolvere il nome simbolico del destinatario. Il trasferimento viene fatto con SMTP a livello 5 e TCP al livello 4
Il destinatario usera IMAP/POP 3 per aggiornare le mail in arrivo (Si occupa della ricezione e sincronizzazione)