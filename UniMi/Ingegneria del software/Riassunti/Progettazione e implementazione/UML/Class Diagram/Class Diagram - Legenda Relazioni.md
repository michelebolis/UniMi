La direzione delle frecce indica il senso della relazione mentre `minimo...massimo` numero di istanze
Tipi:

- Freccia bianca tratteggiata da classe a interfaccia: la classe implementa l'interfaccia
![[Pasted image 20231213104518.png]]
- Freccia con rombo da classe a classe: legame tra istanze, (se bidirezionale non metto la freccia)
	- associazione: la classe ha una dipendenza gerarchica rispetto all'altra 
		![[Pasted image 20231213103909.png]]
	- aggregazione (rombo bianco): indica una relazione NON tra classi ma tra istanze
		Metodo implementativo: l'attributo
		![[Pasted image 20231213104044.png]]
	- composizione (rombo nero): indica un contenimento fisico cioe senza l'uno l'altro non esisterebbe e viceversa. Requisiti:
		- L'oggetto contenuto deve essere presente nella SOLA classe contenente 
		- La vita dell'oggetto contenuto sia legata al contenente 
		Metodo implementativo: classe statica inner
		![[Pasted image 20231213104437.png]]

