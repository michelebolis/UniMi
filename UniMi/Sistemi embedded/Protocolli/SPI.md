**SPI (Serial Peripheral Interface)** è la specifica di un bus per la ==comunicazione seriale sincrona master/slave e non multi-master==.
Quando il clock viene abilitato dal master, vengono trasmessi i dati in seriale.
Solitamente non vi è altra condizione di inizio/fine trasmissione.

Linee bus:
* SCLK (Serial CLoK): segnale attivo-alto inviato dal master che controlla lo spostamento dei bit tra master e slave
* MISO (Master Input Slave Output) attivo-alto
* MOSI (Master Output Slave Input) attivo-alto
* CS (Chip Select): seleziona quale slave abilitare per la comunicazione con il master (abilitato/disabilitato molto distante dalla trasmissione). 
	Quando il clock viene abilitato dal master, vengono trasmessi i dati in seriale (non vi è altra condizione di inizio/fine trasmissione).
	Fondamentale nel controllo e la comunicazione tra un micro-controllore e dei dispositivi periferici (sostanzialmente non fa altro che consentire al micro-controllore di selezionare in modo specifico con quale dispositivo periferico interagire in un dato momento).

![[Pasted image 20230929133655.png]]