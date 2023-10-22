- #Affidabilita: se A manda un contenuto a S o viceversa, quel trasferimento è privo di errori. 
	L'affidabilità, oltre ai messaggi, riguarda anche l'identificazione del malfunzionamento di un link.
	Ci possono essere diversi livelli di tolleranza dell'errore (verra demandata al TCP, affidabile se END to END)

	Tipi di allocazione
	- allocazione a commutazione di circuito: è richiesta una comunicazione completa, senza interruzione del traffico (es voce)
	- allocazione a commutazione di pacchetto: come condividere i canali a disposizione dei vari host
		Usiamo tecniche di multiplexing per condividere i canali da piu host 
		- time division multiplexing TDM: usata nell'ambito delle reti fisse, in particolare per l upload. MA non tiene conto della priorità
	Controllo per garantire l'affidabilità della rete
	- Controllo di flusso: 
	Il protocollo tra A e B deve essere in grado di comunicare a A di aspettare perche B sta processando (o perche ha il buffer pieno) o di far negoziare tra A e B il tempo massimo di elaborazione in base all host piu lento
	es dopo poche interazione HB arriva ad avere il buffer pieno ed inizia a buttare via ciò che gli arriva 
	- Controllo di congestione: 
	La rete deve essere in grado di comunicare quando è congestionata. 
	Una congestione avviene quando si ha una saturazione delle code dei router o ci sono dei link che causano colli di bottiglia (che si notano con l aumento dei pacchetti inviati). 
	Tipi di algoritmi per la congestione:
	- cercano di evitarla a priori
	- aspettano finche non avviene una congestione, cercando di rimediare abbassando la velocita di trasmissione
	Solitamente la perdita di pacchetti è causata da una congestione

- #Sicurezza: ma non è un problema di chi progetta la rete, è di chi progetta l'applicazione
- #Prestazioni: misurabili 
	- nella **velocità di trasferimento** in funzione del bit rate dei canali
	- ... verificare se la mia rete riesce ad erogare all'utente finale la velocita promessa
- #Indirizzamento: la rete deve poter indirizzare il contenuto al destinatario connesso. 
	==Ogni destinatario o mittente deve essere indirizzabile==. 
- #Instradamento: 
- Qualità di servizio #QoS: deve riuscire ad erogare i servizi date le specifiche dell'applicazione (es tempo massimo, tolleranza degli errori...). 
	La rete deve essere il piu possibile general purpose per offrire diverse qualità di servizi in base all applicazione utente. La rete fornisce gli strumenti per essere configurata dalle varie applicazioni, quindi deve essere abbastanza flessibile da potersi adattare alle richieste degli applicativi.
	
	Le richieste/parametri di qualità di servizi sono il Jitter, il data rate, il massimo degli utenti...
	SE non c è la possibilita di raggiungere le richieste, si attua una negoziazione
	
	Difficolta: le applicazioni che utilizzano la rete sono moltissime e molto variegate
	E' necessario che il router applichi una politica per la gestione delle code, per far ciò nel pacchetto i parametri di QoS sono presenti nell'header o sono presenti dei bit per identificare la classe di QoS a cui appartiene il pacchetto