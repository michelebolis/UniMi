Protocollo CSMA-CD Carrier Sense Multiple Access - Collision Detection 
Standardizzato come IEEE 802.3

Quando una stazione vuole trasmettere, prima di farlo fa $Carrier Sense$, cioè legge dal canale ciò che passa, rilevando se il canale sia in idle o meno.

Una collisione si verifica quando due o piu stazioni provano a trasmettere un frame sul bus nello stesso tempo. 
La probabilità di collisione è tanto maggiore tanto piu stazioni ci sono sul canale.

Le collisioni si possono ancora verificare quando SE una stazione B sta trasmettendo e una stazione C fa CS, quest'ultima aspetta che B finisca. Tuttavia se un altro nodo A fa CS, sia A che C stanno aspettando la terminazione della comunicazione di B ed causando ancora una collisione

Quanto aspettare prima di una ritrasmissione: [[BEB -Binary Exponential Backoff]]

Tutti i frame sono trasmessi usando la [[Codifica di Manchester]]

Formato dei frame
- Il SFD Start Of Frame Delimiter è composto da un singolo byte 10101011
- L'indirizzo del destinatario e del mittente come indirizzi MAC, che identificano l'interfaccia HW del destinatario e del mittente
- Vi sono poi due byte dedicati alla lunghezza/type che indica la lunghezza del payload
	SE questa lunghezza è minore del minimo richiesto per un frame valido, allora viene aggiunta una sequenza di byte, padding
- Infine FCS contiene un CRC value per rilevare l errore

[[Standard rete a 10Mbps]]
[[Standard rete a 1Gbps]]