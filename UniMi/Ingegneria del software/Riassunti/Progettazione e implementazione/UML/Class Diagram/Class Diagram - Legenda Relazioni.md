La direzione delle frecce indica il senso della relazione mentre `minimo...massimo` numero di istanze
Legami tra classi:
- `generalizzazione`: linea continua e triangolo bianco (`extendes`)
- `realizzaione`: linea tratteggiata e triangolo bianco (`implements`)
![[Pasted image 20231213104518.png]]

Legami tra istanze
- `composizione`: rombo nero, indica un contenimento fisico cioe senza l'uno l'altro non esisterebbe e viceversa (`classe statica inner`). Requisiti:
	- L'oggetto contenuto deve essere presente nella SOLA classe contenente 
	- La vita dell'oggetto contenuto sia legata al contenente 
![[Pasted image 20231213104437.png]]
- `aggregazione`: rombo bianco, indica una relazione NON tra classi ma tra istanze (`attributo`)
![[Pasted image 20231213104044.png]]
- `dipendenza`: linea tratteggiata con freccia nera, parte del codice viene utilizzato MA non salvato a livello di istanza
![[Pasted image 20231213103909.png]]
- `associazione`: linea continua con freccia nera, quando se cambio il codice di una classe, dovro anche cambiare il codice dell'altra MA non è detto che si conoscano (es classe che salva dati in un file e classe che legge da un file, si differenziano per la codifica
![[Pasted image 20240209101025.png|300]]