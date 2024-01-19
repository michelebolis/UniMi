Un email client è un SW chiamato `UA User Agent` che fornisce un interfaccia utente per creare, inviare e ricevere mail 
UA mantiene una mailbox in IN e OUT. Il SW associato alla funzione di invio è chiamato `MTA Message Transfer Agent`

Protocollo per l'invio: `SMTP Simple Mail Transport Protocol`
Protocollo per la ricezione:
- `POP 3`: fa operazioni elementali come prendere la posta dal server ed ha un'unica coda delle mail
- [[IMAP]] 

| Protocollo                   | Numero di porta                           |
| ---------------------------- | ----------------------------------------- |
| POP 3 (Post Office Protocol) | 110/995                                   |
| IMAP                         | 143/993 (socket non sicure/socket sicure) |
| SMTP                             |25/2525/587 (TLS esplicito cioe connessione sicura)/465 (TLS implicito)                                           |
 
[[Email - Formato]]
[[Email - Invio e ricezione]]