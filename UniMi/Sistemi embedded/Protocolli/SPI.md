 **SPI (Serial Peripheral Interface)** è la specifica di un bus per la comunicazione seriale sincrona master/slave e non multi-master.
 Linee bus:

* SCLK (Serial CLoK): segnale attivo-alto inviato dal master che controlla lo spostamento dei vit tra master e slave
* MISO (Master Input Slave Output) attivo-alto
* MOSI (Master Output Slave Input) attivo-alto
* CS (Chip Select): seleziona quale slave abilitare per la comunicazione con il master (abilitato/disabilitato molto distante dalla trasmissione). Per apprezzarne  la variazione dovremmo prevederne l'attivazione e la disattivazione molto prima e molto dopo allla trasmizzione. Tuttavia cosi non sarebbe permesso vedere altri segnali distintamente.
 Quando il clock viene abilitato dal master, vengono trasmessi i dati in seriale.
 Solitamente non vi è altra condizione di inizio/fine trasmissione.