I più moderni sistemi per il riconoscimento basati sull'iride rappresentano l'iride come una stringa di bit, spesso chiamata IRISCODE . Di conseguenza si passa dall'immagine dell'iride al template (IRIS CODE).

Si tratta di un problema molto complesso, affinché la conversione avvenga correttamente moltissimi fattori sono da tenere in conto.

Passi che ci permettono di passare da una immagine di un occhio ad un IRISCODE:
- Individuare dei centri e raggi della pupilla e dell'iride :
	- Per prima cosa bisogna andare ad identificare l'occhio in un immagine del volto.
	- Eseguire una acquisizione corretta dell'iride ( almeno 70 pixel a fuoco, lungo il raggio)
	- Trovare la pupilla
	- Trovare il raggio esterno dell'iride e rifinire le stime.
- Rimozione della parte non utile occupata dalle iridi e dalle ciglia :
	- Solo una parte dell'iride è utile al riconoscimento
	- Occore segmentare la parte utile dell'iride "marcando" l'immagine dove invece sono presenti ciglia, palpebre, riflessi esterni, ecc..
	- Se manca più del 50% dell'iride occorre riacquisirla
- Linearizzazione dell'iride :
	- Individuati i raggi e centri si procede alla fase i unwrapping dell'iride ( linearizzazione)
	- Si fissano le dimensione dei settori dell'iride
	- Ogni pixel dell'iride linearizzata nasce da una interpolazione del corrispondente settore dell'iride .
- Trasformazione della iride linearizzata in IRSCODE :
	- Avendo l'iride linearizzata I espressa nelle coordinate P(raggio) e Teta (angolo), si calcolo attraverso una specifica formula la convulazione dell'iride con delle funzioni gaussiane.
	Vengono utilizzate delle wavevelt come filtro.
	- Il modello dettagliato dell'iride è codificato in un "IrisCode" di 256 byte  
	    demodulandolo con 2D Gabor wavelet. Viene trovato un quadrante per  
	    ogni elemento locale dell'iride modello,  questa operazione è  
	    ripetuto in tutto l'iride, a molte scale diverse

Sempre partendo dalla linearizzazione dell’iride esistono altri modi di produrre tipi diversi di “iriscode” rispetto a quello di Dougman (SmartSensors LTD)


Proprietà dell'IRIS CODE :
La codifica dell'iride è eseguita in uno spazio 2D a-dimensionale di coordinate polari, questo permette di rendere la codifica invariante rispetto :
- Alla dimensione dell'iride
- Allo zoom dei sistemi ottici
- Alla dilatazione dell'iride dovuta alla luce

Le funzioni wavelet usate in demodulazione sono parametrizzate con 4 grandi libertà ( dimensione, orientamento) che possono variare in alcune ottave ( raddoppio della dimensione). Questo permette di garantire più scale di dettagli che verranno colte nella codifica.

Si tratta di una codifica molto compatta, in genere bastano 256 byte per rappresentare un iride, tutta via bisogna aggiungere 256 bit di controllo per escludere i bit nati da artefatti, dovuti a :
- Riflessi delle luci ambientali sull'iride ( in realtà sulla coronea)
- Ciglia sovrapposte
- Palpebre
- Regioni con troppo poco contrasto.

L'iris Code è inoltre un codice a massima entropia, la probabilità di ogni bit dell'IRIS CODE di essere 1 è del 50%


Non esiste solo IRISCODE per rappresentare un iride
Metodi di rappresentazioni dell’iride in un sistema biometrico in letteratura:
- Daugman Gabor Demodulation (PAMI 1993)
- Lim, Lee, Byeon , Kim, Wavelet Features (ETRIJ 2001)

In letteratura stanno iniziando ad essere usati approcci di segmentazione, estrazione template e matching basati su reti di Deep Learning (performanti, ma non adatti a usi in dispositivi embedded o con DB di grandi dimensioni)
- Abdolrashidi DeepIris : Iris Recognition Using A Deep Learning Approach (CVPR 2019)


