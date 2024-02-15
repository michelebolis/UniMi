Primo passo della catena, occorre` rintracciare il volto/i volti da una scena senza alcun prerequisito particolare`. Si tratta di un problema molto complesso, in quanto nell'immagine possono cambiare :
- Condizioni di luce
- Colore
- Posizione dei volti
- Espressione dei volti
- Posa dei volti

I risultati ad oggi migliori si ottengono con degli `algoritmi di deep learning`. Tuttavia è bene notare che non tutte le applicazioni possono permettersi di usare modelli di deep learnign.
Per questo motivo, abbiamo anche bisogno di approcci più "basilari".
Molti approcci sono basati su modelli molto semplici del volto: in termini geometrici o di texture

Questi modelli permettono di `trovare nelle immagini le regioni che fittano meglio il modello` dove è maggiore probabilità che vi sia un volto.

L'obbiettivo è quello di `individuare il volto / i volti nella scena per arrivare a ricostruire l'immagine sul piano normale` a quello osservazionale attraverso quali :
- Stima dei parametri del volto
- Correzione di scala e traslazione
- Rotazione


1. `Face-Detection Color based`
	Nel caso di immagini a colori uno degli schemi più diffusi è il seguente
	- `Lightin compensation`
	- `Skin tone detection`
	La skin tone detection viene effettuata `controllando quali bit dell'immagine appartengono ad una regione determinata dello spazio colore che evidenza meglio le differenze`.
	
	Vengono messi a 1 i pixel che appartengono a una regione dello spazio colore. In questo modo si riesce ad evidenziare il contorno della faccia.
	![[Pasted image 20231115094210.png|300]]
	
	- `Localization of facial features` ( occhi. Bocca, contorno del viso) :
	La rilevazione della posizione degli occhi e della bocca viene effettuata `sottraendo immagini espresse in appositi spazi colore` ( Y,Cr,Cb) che ne possano mettere in evidenza le caratteristiche cromatiche peculiari insieme a filtraggi morfologici.
	- `Aggregazione dei risultati`
2. `Face detection - Harr feature`
	Si tratta di un metodo basato sulle `funzioni di Haar`. Consiste nel cercare nelle immagini, delle regioni che presentano particolari valor delle trasformate di haar.
	
	Solitamente i `volti sono caratterizzati da particolari valori` e quindi si possono trovare mediante dei classificatori. Le trasformate di haar sono funzioni che prendono il valore di differenze fra i valori di grigio di 2/3 zone ( di area, posizione ed orientamento diverso).
	
	Le posizioni dei massimi ed i massimi delle trasformate sono caratteristiche utili per decidere se è presente un volto nell'immagine di partenza.
	Esistono varie trasformate con diversa forma e orientamento.

`Quando invece abbiamo un video in input e non più un immagine, allora si parla di face tracking`. Non è esattamente come fare face detection in ogni frame, in quanto si hanno maggiori informazioni.
Avendo almeno due frame è possibile effettuare una previsione sullo spostamento del volto.