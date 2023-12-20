Protocollo CSMA-CD Carrier Sense Multiple Access - Collision Detection 
Standardizzato come IEEE 802.3

Quando una stazione vuole trasmettere, prima di farlo fa $Carrier Sense$, cioè legge dal canale ciò che passa, rilevando se il canale sia in idle o meno.

Una collisione si verifica quando due o piu stazioni provano a trasmettere un frame sul bus nello stesso tempo. 
La probabilità di collisione è tanto maggiore tanto piu stazioni ci sono sul canale.

Le collisioni si possono ancora verificare quando SE una stazione B sta trasmettendo e una stazione C fa CS, quest'ultima aspetta che B finisca. Tuttavia se un altro nodo A fa CS, sia A che C stanno aspettando la terminazione della comunicazione di B e cio causa ancora una collisione

![[photo_5769355704325488862_y.jpg|600]]

Per risolvere la collisione, prima di ritrasmettere, ogni nodo aspetta un tempo determinato dal  [[BEB -Binary Exponential Backoff]]

Tutti i frame sono trasmessi usando la [[Codifica di Manchester]]

Formato dei frame

| Campo            | Dimensione | Descrizione                                                                                                                |
| ---------------- | ---------- | -------------------------------------------------------------------------------------------------------------------------- |
| SFD              | 10101011   | Start Of Frame Delimiter indica l'inizio                                                                                   |
| MAC destinatario | 48 bit     |                                                                                                                            |
| MAC sorgente     | 48 bit     |                                                                                                                            |
| Type/length      | 16 bit     | SE questa lunghezza è minore del minimo richiesto per un frame valido, allora viene aggiunta una sequenza di byte, padding |
| Data             |            |                                                                                                                            |
| FCS              | 32 bit     | contiene un CRC value per rilevare l errore                                                                                |


![[Pasted image 20231219133605.png|500]]

[[Standard rete a 10Mbps]]
[[Standard rete a 1Gbps]]