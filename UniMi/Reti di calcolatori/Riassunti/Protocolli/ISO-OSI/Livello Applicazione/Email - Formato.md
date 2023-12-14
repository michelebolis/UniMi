Formato logico
Separazione tra header e body fatta da UA con una linea vuota (\\n\\n), usando TCP non c è una separazione ma è tutto byte stream quindi viene fatto al livello 5
- Usato MTS System: 
	- Messi dallo UA: from, to, Cc (Carbon copy), BCC (Blind Carbon Copy non è esplicito agli altri che ho ricevuto anche io la mail)
	- Messi nell header man mano che la mail procede: received (per avere la traccia che ha percorsa la mail), Return-Past (ultimo MTA)
- Usato da UA: sender, date, message-id (id messo dallo UA), reply-to (usera questa mail invece che from se il destinatario vuole rispondere), oggetto
- X-...: header definiti dall'utente es X-PhoneNumber

I campi dell'header sono letteralmente "To: nome@dominio
[[Email - Contenuto]]