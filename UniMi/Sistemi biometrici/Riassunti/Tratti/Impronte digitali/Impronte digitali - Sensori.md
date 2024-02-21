Qual è il compito dei sensori :
- I sensori devono cercare di catturare la distribuzione di creste e valli sulla pelle .
- Maggiori dettagli catturiamo, migliore sarà la capacità del sistema di identificare/verificare le identità delle persone.
- Possiamo immaginare le impronte come immagini bidimensionali ma anche come superfici tridimensionali.

Tipologie di sensori e caratteristiche :
Esistono due modalità di acquisizione fondamentali :
- `Off-line`:
L'acquisizione off-line è divisa in due fasi fondamentali :
- I polpastrelli vengono prima passati su un tampone inchiostrato e poi vengono rotolati su una scheda di carta
- La scheda di acquisizione viene acquisita con uno scanner ottico o telecamera ad alta risoluzione.

Le `impronte digitali latenti`, sono di tipo off-line ( Ad esempio le impronte trovare su una scena del crimine). Sono prodotte dalle `tracce lasciate dal grasso secreto della pela`,  esso lascia sulle superfici una traccia evidenziabile con speciali reagenti chimici
- `Live - Scan`:
Nella modalità live scan, invece l'immagine digitale dell'impronta è `acquisita in tempo reale`, tramite il contatto del polpastrello con un apposito sensore

I sensori possono essere :
- `Ottici`, Basati su :
	- Fenomeno della frustated total internal reflection
	- Su scanner tradizionali
	Sfruttano delle `proprietà di rifrazione della luce` su un condensatore che cattura le informazioni.
- `Stato solido`, con pixel sensibili alle variazioni di :
	- Capacità
	- Pressione
	- Temperature
Il contatto fra il ridge e la superficie del sensore cambia la capacità del circuito e del singolo pixel. I Sensori a stato solido che rilevano la temperatura o la pressione hanno forma simile ma circuiti dedicati diversi per il singolo pixel.
- Ultrasuoni
- Sensori 3D 
Esistono dei `sensori che riescono a rilevare la tridimensionalità della impronta digitale`.
Nel futuro potranno giocare un ruolo fondamentale se si dimostra che hanno un accuratezza migliore rispetto a quella dei sensori attuali.
Offrono maggiore resistenza agli attacchi


I vari sensori produco delle immagino con delle caratteristiche molto diverse fra loro, `i sensori di tipo termico producono l'immagine più accurata possibile`.

Un buon sensore per l'acquisizione di un impronta digitale deve godere delle seguenti proprietà :
- Risoluzione
- Area di acquisizione
- Numero di pixel e bit per pixel
- Contrato
- Distorsione geometrica

In alcune applicazione, oltre alle caratteristiche citate in precedenza può essere utile tenere in considerazione anche i seguenti parametri :
- Numero di frame per secondo
- Presenza meccanismi HW/SW sul sensore per il rilevamento automatico della presenza del dito e delle condizioni. Il sensore effettua l'acquisizione solo se si verificano le condizioni ideali.
- Supporto per comunicazioni crittate
- Sistemi operativi supportati, driver
- Librerie e presenza di documentazione

Esempi di alcuni sensori commerciali

| None                        | Risoluzione               | Velocità | Caratteristiche      |
| --------------------------- | ------------------------- | -------- | -------------------- |
| Google nexus 6p fingerprint | 508 dpi (160\*160 pixels) | 600 ms   | Dry/wet fingerprints |
|Iphone6 finger sensor|500dp|170 um|Lavora anche con protezione|
|Synptics sensor|||Tecnologia under the glass, rende il sensore meno invasivo|

Esempio di sistema multimodale
![[Pasted image 20231106102658.png|100]]
TVIP4FF= Si tratta di un sistema multimodale in grado di eseguire Facial recognition, riconoscimento impronta digitale, RFID, pin.
- Ha delle ottime performance e accuratezza
- Live finger detection
- Ha una capacità di 4000 impronte digitali, 2000 facce e 10.000 card credentials


Problemi di acquisizione
Nella fase di acquisizione, si possono verificare una serie di problematiche :
- `Pressione del dito`: come cambia un impronta con una maggiore o minore pressione del dito sul sensore :
	- I ridge da discontinui tendono a diventare continui
	- Iniziano a vedersi:
		- I pori sono sempre presenti
		- Incipients ridge ( presenti nel 45% della popolazione (*)
	- Quando la pressione diventa troppa, iniziano ad unirsi i ridge fra loro con gli incipients ridge.
	![[Pasted image 20231106102733.png|300]]

- `Roto traslazioni e deformazioni`
Le parti in contatto con il sensore tendono a non ruotare/spostarsi con il dito, creando una deformazione non lineare, creando così una roto-traslazione.
![[Pasted image 20231106102749.png]]
