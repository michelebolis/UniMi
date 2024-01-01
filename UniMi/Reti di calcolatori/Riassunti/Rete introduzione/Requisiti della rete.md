- [[Affidabilita]]: se un nodo A manda un contenuto a un nodo S o viceversa, quel trasferimento è privo di errori. 
- Sicurezza: ma non è un problema di chi progetta la rete, è di chi progetta l'applicazione
- Prestazioni: misurabili 
	- nella **velocità di trasferimento** in funzione del bit rate dei canali
	- verificare se la mia rete riesce ad erogare all'utente finale la velocita promessa
- Indirizzamento: la rete deve poter indirizzare il contenuto al destinatario connesso. Ogni destinatario o mittente deve essere indirizzabile. 
- Instradamento
- Qualità di servizio QoS
	La rete deve essere il piu possibile general purpose per offrire diverse qualità di servizi in base all'applicazione utente. La rete fornisce gli strumenti per essere configurata dalle varie applicazioni, quindi deve essere abbastanza flessibile da potersi adattare alle richieste degli applicativi.
	
	Le richieste/parametri di qualità di servizi sono il Jitter, il data rate, il massimo degli utenti...
	SE non c'è la possibilita di raggiungere le richieste, si attua una negoziazione.
	QoS sono definiti mediante classi di servizi a cui viene assegnata una relativa priorità
	
	Difficoltà: le applicazioni che utilizzano la rete sono moltissime e molto variegate
	E' necessario che il router applichi una politica per la gestione delle code, per far ciò nel pacchetto i parametri di QoS sono presenti nell'header o sono presenti dei bit per identificare la classe di QoS a cui appartiene il pacchetto