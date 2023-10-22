I router consentono di trovare il percorso migliore per raggiungere una destinazione in quel momento.

Un router ha delle linee di ingresso e delle linee d'uscita, entrambi bidirezionali (porte I/O), associate a code (FIFO) di dimensione fissa. 

I problemi sono il numero di porte e la velocita in cui operano i link di uscita e ingresso.
SE una delle code/buffer è pieno, butto via il contenuto. Uno dei problemi dei router è la gestione della memoria. 

Si decise quindi di ==frammentare il contenuto in dimensioni massime fisse== creando #pacchetti in modo da avere una gestione del traffico semplificata. 
Questa frammentazione deve avvenire lato del mittente, aggiungendo un #header o intestazione con delle informazioni necessarie per il funzionamento della rete, quali l indirizzo. 

I router ha un piccolo SW di instradamento che periodicamente, facendo una codifica dei pacchetti (in particolare lo header che sicuramente contiene sorgente e destinazione), decide in che porta mandare il pacchetto. secondo la tabella di instradamento. La tabella di instradamento infatti contiene dato un destinatario, la porta di uscita associata che permette di seguire il percorso migliore per ogni indirizzo raggiungibile.

Piu piccoli sono i pacchetti, meno spazio occuperemo nelle code ma avremo un overhead a causa dell'header di ogni pacchetto. 
Serve un compromesso tra lo spazio occupato nelle code e l'overhead

Man mano che il pacchetto viene processato dai router, aumenta di dimensione, diminuendo quando arriva al destinatario (fragmentation-assembly-deassembly)

La sequenza prelevamento-decodifica-forward deve essere effettuata il piu velocemente possibile. Difatti l'header è posizionato nei primi bit cosi il router sia piu veloce nella lettura