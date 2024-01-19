Protocollo `CSMA-CD Carrier Sense Multiple Access - Collision Detection `
Standardizzato come `IEEE 802.3`: [[CSMA-CD - Formato]]

Quando una stazione vuole trasmettere, prima di farlo fa `Carrier Sense`, cioè legge dal canale ciò che passa, rilevando se il canale sia in idle o meno.

La probabilità di collisione è tanto maggiore tanto piu stazioni ci sono sul canale.
Le collisioni si possono ancora verificare SE una stazione $B$ sta trasmettendo e una stazione $C$ fa CS, quest'ultima aspetta che $B$ finisca. Tuttavia se un altro nodo $A$ fa CS, sia $A$ che $C$ stanno aspettando la terminazione della comunicazione di $B$ e ciò causa ancora una collisione

![[photo_5769355704325488862_y.jpg|600]]

Per risolvere la collisione, prima di ritrasmettere, ogni nodo aspetta un tempo determinato dal  [[BEB -Binary Exponential Backoff]]

Tutti i frame sono trasmessi usando la [[Codifica di Manchester]]
[[Standard rete a 10Mbps]]
[[Standard rete a 1Gbps]]