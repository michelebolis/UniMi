* **lampadina attaccata a coppia di fili collegati a dei morsetti**: si collega un morsetto a masse e l'altro lo si attacca nelle varie parti del circuito. Se arriva tensione la lampadina ci accenderà. La lampadina deve essere scelta in modo che possa accendersi alla tensione desiderata.
 Nell'ambito embedded si una il led anziché la lampadina, nel caso munito di resistenze se la tensione è troppo alta.  
 Se la lampadina è collegata in serie ad una batteria allora la si può usare per testare la continuità. Es su un cavi interrato, senza dissotterrarlo, cortocircuito i capi inserendoci in mezzo il "tester". Se la lampadina si accende il cavo è a posto.
* #voltmetro: strumento che misura la tensione tra di punti di un circuito. Lavora in _**parallelo**_. 
	Serve a capire se ci sono parti insufficientemente alimentate o non alimentate.
* #amperometro: strumento che si inserisce in serie e misura l'intensità di corrente passante. Serve per misurare l'intensità, stimare il consumo e per valutare la potenza impiegata con la legge di Ohm $P=R*I^2$. 
	Ha resistenza bassissima per interferire il meno possibile con le misurazioni. 
	Se collegato ad una fonte di alimentazione saltano le protezioni (se le ha) o si fondono i cavi,
	* #pinza-amperomentrica: tipo di amperometro usabile in parallelo. Le due ganasce della pinza si chiudono su un file e minurano per induzione elettromagnetica su correnti alternate.
* #ohmometro: misura i valori di resistenza e lo si può usare per valutare la condizione di una giunzione (diodi e transistor):
	- giunzione interrotta: resistenza infinita in entrambi i sensi
	- giunzione in corto: resistenza zero in entrambi i sensi
	- giunzione possibilmente a posto: resistenza infinita in un senso e zero nell'altro
	 è uno strumento attivo composto da un amperometro e una pila che fornisce tensione. Viene immessa la tensione di regime al componente da valutare e misurando la corrente (intensità) che scorre nel circuito e usato la legge di Ohm $R_{incognita}=\frac{V_{immessa}}{I_{misurata}}$
* #multimetro: strumento che integra i vari strumenti di misura.
* #oscilloscopio: misura le forme d'onda. se collegato a due punti di un circuito plotta su un display il grafico dell'andamento della tensione. 
	Solitamente hanno più ingressi per poter confrontare più forme d'onda contemporaneamente.
