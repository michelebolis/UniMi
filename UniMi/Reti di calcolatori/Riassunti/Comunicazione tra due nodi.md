Ogni router ha porte I/O, ognuna con una coda (FIFO) di entrata e una coda in uscita
Periodicamente secondo un algoritmo di instradamento, facendo una codifica dei pacchetti (in particolare lo header che sicuramente contiene sorgente e destinazione), decide in che porta mandare il pacchetto. secondo la tabella di instradamento. Essa infatti contiene dato un destinatario, la porta di uscita associata

Le code hanno una dimensione finita
La sequenza prelevamento-decodifica-forward deve essere effettuata il piu velocemente possibile. Difatti l'header è nei primi bit cosi il router è piu veloce nella lettura
Piu piccoli sono i pacchetti, meno spazio occuperemo nelle code ma avremo un overhead a causa dell'header di ogni pacchetto. 
Serve un compromesso tra lo spazio occupato nelle code e l'overhead


[[Tempi della trasmissione]]


Trasmissione in banda base: quando trasmetto da 0 a Hz massimo 
ogni canale fisico ha un certo data-rate, rate di immissione 
es 1 Mbps
attaccata alla porta di rete abbiamo il bus di comunicazione con la coda di uscita $T_x$, con delle word di una certa dimensione.
Viene quindi fatta una prima conversione mandando in alternanza veloce i singoli bit (da LSB a MSB), grazie a un clock. 
es di protocollo: Lato ricevitore si rappresenta l'1 con un livello alto di voltaggio e 0 un voltaggio basso. 
Problemi: 
- Essendo pero due sistemi distribuiti, hanno due clock diversi: è necessario capire quando inizia e quando finisce un bit, saranno quindi necessari algoritmi di sincronizzazione

Tipicamente la rete non è affidabile a causa del rumore. In realta per la maggior parte dei casi non è richiesta affidabilita ma piuttosto la velocita (es voce in videochiamata, caso contrario una mail)
Un bit potrebbe cambiare nel suo opposto
Ci sono bit aggiuntivi per
- riconoscere se c e stato almeno un bit sbagliato
- O eventualmente rimediare all'errore

La rete deve quindi essere in grado di riconoscere se un pacchetto è corretto/non alterato e rimediare all errore. SE la rete è affidabile e succedono degli errori, siamo in grado di risolverli dagli host (non dalla rete)
Nel caso in cui il pacchetto sia arrivato corretto, ma la consegna dei singoli pacchetti non è in ordine, è necessario un meccanismo per ricomporli. In particolare oltre a sorgente e destinazione, si puo avere una serie di bit per riconoscere la posizione del pacchetto nella sequenza e la lunghezza totale della sequenza.
Potrò quindi anche riconoscere se ho ricevuto dei duplicati

Il ricevente manda al mittente un Acknoledgement (ACK) ogni volta che riceve un pacchetto corretto.
A entra in uno stato di Idle una volta che ha mandato i bit da $T_x$ ; durante questo tempo il canale non è utilizzato.


Una volta inviato un pacchetto, ne tengo una copia nel buffer del Kernel finchè non mi ricevo ACK. Stessa cosa anche il ricevente, tiene una copia del pacchetto nel buffer del Kernel finchè non riceve tutti i pacchetti del file.
Una volta inviato un pacchetto, parte un timer per il Waiting che stima il tempo minimo, cioè $T_x + 2*T_p$ sovrastimato

SE ACK non arriva, in quanto potrebbe essere perso o corrotto, A non sa se è arrivato il pacchetto, quindi lo manda nuovamente. 
L'Host ricevente riconosce se il pacchetto fosse gia arrivato nei buff. Nel caso ce l'abbia già lo scarta, mandando lo stesso l'ACK al mittente.


La rete fornisce gli strumenti per essere configurata dalle varie applicazioni, quindi deve essere abbastanza flessibile da potersi adattare alle richieste degli applicativi.

Un protocollo è un insieme di regole e convenzioni che permettono la comunicazione tra due entità. Ovviamente le due entità devono usare lo stesso protocollo.