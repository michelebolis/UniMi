Formato logico
L'indirizzo mail è considerato come un `domain name` formato da due parti  separate dalla `@`

Il messaggio è composta da un header e da un body separati da una linea vuota (`\n\n`), infatti usando TCP non c'è una separazione ma è tutto byte stream quindi viene fatto al livello 5
- Usato `MTSystem`: 
	- Messi dallo UA: from, to, Cc (Carbon copy), BCC (Blind Carbon Copy non è esplicito agli altri che ho ricevuto anche io la mail)
	- Messi nell'header man mano che la mail procede: received (per avere la traccia che ha percorsa la mail), Return-Past (ultimo MTA)
- Usato da UA: sender, date, message-id (id messo dallo UA), reply-to (usera questa mail invece che from se il destinatario vuole rispondere), oggetto
- X-...: header definiti dall'utente es X-PhoneNumber

`Ogni campo nell'header comprende una singola linea di un testo ASCII `con il nome del campo (standardizzato) (es "To: nome@dominio")
Per rappresentare la EOL si utilizza un CR Carriage return e un LF Line Feed
[[Email - Contenuto]]