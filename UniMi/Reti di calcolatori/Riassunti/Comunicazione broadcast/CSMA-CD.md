Protocollo CSMA-CD Carrier Sense Multiple Access - Collision Detection 
Standardizzato come IEEE 802.3

Quando una stazione vuole trasmettere, prima di farlo fa $Carrier Sense$, cioè legge dal canale ciò che passa, capendo se è il canale è in idle o meno.

Una collisione si verifica quando due o piu stazioni provano a trasmettere un frame sul bus nello stesso tempo. 
La probabilità di collisione è tanto maggiore tanto piu stazioni ci sono sul canale.

Le collisioni si possono ancora verificare quando SE una stazione B sta trasmettendo e una stazione C fa CS, quest'ultima aspetta che B finisca. Tuttavia se un altro nodo A fa CS, sia A che C stanno aspettando la terminazione della comunicazione di B ed causando ancora una collisione

La ritrasmissione dei frame coinvolti nella collisione avviene quindi dopo un tempo $\tau$ casuale ottenuto con la tecnica BEB
$$BinaryExponenzial Backoff(BEB) = [0:2^i-1]*UT$$
con i il numero di collisioni (1<i<16) della stazione e UT unita di tempo 

Potrebbero ancora collidere se viene generato lo stesso numero di UT ma è probabilistico
CSMA/CD NON garantisce che il frame che arriva senza collisioni sia senza errori

Tutti i frame sono trasmessi usando la [[Codifica di Manchester]]

Formato dei frame
- Il SFD Start Of Frame Delimiter è composto da un singolo byte 10101011
- L'indirizzo del destinatario e del mittente sono indirizzi MAC, che identificano l'interfaccia HW del destinatario e del mittente
- Vi sono poi due byte dedicati alla lunghezza/type che indica la lunghezza del payload
	SE questa lunghezza è minore del minimo richiesto per un frame valido, allora viene aggiunta una sequenza di byte, padding
	La massima dimensione del payload è invece di 1500bytes
- Infine FCS contiene un CRC value per rilevare l errore

[[Standard rete a 10Mbps]]
[[Standard rete a 1Gbps]]