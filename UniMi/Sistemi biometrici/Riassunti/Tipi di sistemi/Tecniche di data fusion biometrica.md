Dato che nei sistemi multimodali andiamo ad acquisire più tratti biometrici, in un certo modulo del sistema dovremo andare ad eseguire una `funzione dei vari match score per ogni tratto e decidere se l'utente è autorizzato o meno`.
- Sistemi multimodali :
	- Fusione a livello delle feature
	- Fusione a livello di matchscore ( dopo aver eseguito un matching per ogni tratto)
	- Fusione a livello di Decision module
- Sistemi muti-biometrici
	- Fusione a livello di matchscore
	![[Pasted image 20240214094252.png|300]]


Fusione a livello di matching :
- Nel caso di `sistemi multibiometrici` con lo stesso tratto biometrico, una solo immagine ma diversi moduli di estrazione delle feature, la fusion dopo il matching risulta la soluzione migliore.  Utilizzo più matcher diversi e ne combino i risultati.
![[Pasted image 20240214094306.png]]
- Nel caso di tratti indipendenti tra di loro o stesso tratto ma sample diversi risulta meno efficace.
`Nel caso delle impronte si ottiene il massimo livello di accuratezza usando 3 dita`.

Metodi di fusione del match score :
- `Regola della somma`
	La regola della somma si è sempre rilevato in grado di aumentare le prestazione dei test :
	S = W1S1 + W2S2 + W3S3
	
	Si tratta di un metodo di fusione semplice a livello di match score.
	
	Esistono due filosofie diverse per unire i vari match score s1,s2…sn:
	- `Classificazione`: il classificatore è un modulo che avendo in ingresso i S1,S2,….,Sn `match score produce direttamente l'uscita impostore/genuino`:
		- Reti neurali
		- Questi sistemi per poter fissare i parametri necessitano di dati e di una fase di allenamento ( trainer classsifier).
	- `Regressione/combinatore`: è un modulo che combina in modo lineare, non lineare, logico/combinatorio i valori S1, S2, …,Sn e `passa un univo valore S al decisore finale` ( che può essere di nuovo un calssificatore o una semplice)  :
		- AND/OR funzioni, votazioni, max, min
		- Reti neurali e regressori.
- `Normalizzazione degli score`
	Per confrontare fra loro correttamente i vari valori di diversi matcher ( valori di distanza tra template ) è necessario eseguire prima un operazione di normalizzazione :
	- Omogeneizzare il significato = per esempio s1 è una similarità e s2 è una distanza.
	- Riportare alla stessa scala =  le uscite s1,…sn potrebbero essere su scale diverse, ad esempio s1 potrebbe andare da 0 a 100 e s2 da 0 a 10000
	- Uniformare le distribuzioni dei valori
	
	Meglio tenere conto di :
	- Robustezza, Una valore di matching completamente diverso dagli altri potrebbe essere errato e non deve stravolgere la normalizzazione.
	Mediana e sigmodale in questa categoria
	- Efficienza, occorre normalizzare avendo dei parametri stimati, che però devono essere vicini a quelli reali dei match score, altrimenti la normalizzazione non è corretta.
	
	Rientrano in questa categoria le normalizzazioni min e max
	Occorre provare sempre diverse normalizzazioni per vedere quale permette la percentuale di FAR più bassa.

	![[Pasted image 20240214094438.png|400]]
