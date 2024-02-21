- `Ridge counting`
	`È una misura dei ridge che attraversano una linea immaginaria passante tra due minutiae`
	![[Pasted image 20231106104346.png|300]]
	La grandezza del ridge counting pur essendo calcolata partendo dalle minutiae ( livello 2) è considerato come appartenente al livello 1, in quanto porta informazioni non localizzate attorno ad un punto ma su cosa succede nell'impronta fra alcuni punti anche lontani fra loro.
- `Analisi delle frequenze spaziali`:
	È una misura di `quanto sono stretti o larghi i ridge nelle varie regioni dell'impronta`.
	`Ridge frequency= inverso della distanza media tra due picchi consecutivi`
	
	`Mappa delle frequenze spaziali`: usando l'informazione ricavata dalla frequenze di ridge per ogni blocco dell'immagine è possibile avere la `mappa delle frequenze nell'immagine`
	![[Pasted image 20231106104456.png|300]]
- `Orientamento dei ridge`
	- Non è un calcolo banale
	- Di solito si divide l'immagine dell'impronta in blocchi W x W non sovrapposti. Esiste successivamente una formula che calcola la stima ottimizzata dell'orientamento medio nel blocco.
	- Occorre ora controllare che non vi siano salti di fase, dovuti al fatto che il ridge non ha un verso ma solo la direzione (da 5 a 175) gradi
	In alcuni casi è necessario eseguire un filtraggio passa-basso ( una media spaziale), per evitare comunque salti bruschi vicino ai punti singolari come core e delta.
- Il calcolo esatto e robusto dell'orientamento dei ridge è fondamentale nell'enhacement, nell'identificazione delle minute e nella funzione di matching delle impronte digitali.
	Usando la media di orientamento di ogni blocco ( $\theta(i, j)$), si ottiene una `mappa degli orientamenti`.
	Successivamente si può utilizzare il vettore gradiente dell'immagine in un blocco Bij, per produrre mappe nelle quali si visualizza il vettore ottenuto dal modulo e dall'orientamento del gradiente.
	![[Pasted image 20231106104541.png|300]]
- `Orientation Field Flow Curves`
	Le OFFC sono `curve (sintetiche) all'interno delle impronte digitali`, la cui tangente è parallela al campo di orientamento dell'impronta.
	
	Sono molto `usate per studiare la topologia e per classificare le impronte`. In quanto permettono di localizzare in modo robusto la presenza di punti singolari come core e delta attraverso il loro andamento.
	
	Le OFFC si proiettano in uno spazio attraverso le mappe isometriche. L'andamento della proiezione, individua il tipo di punto singolare
	![[Pasted image 20231106104554.png|300]]

Usando Core/Delta e/0 OFFC si arriva ad una `percentuale di errore del 3% nella classificazione di una impronta`.
Notare come :
- `abbassando il numero di classi` si alzi il numero di campioni necessari da scansionare, il `precision rate tuttavia sale`.

- Core detection
- Metodo delle normali :
I punti di core possono essere calcolati intersecando le normali

Se seguendo N ridge e calcolando M normali abbiamo un numero sufficientemente alto di intersezioni in un introno di un punto allora abbiamo trovato un core.
![[Pasted image 20231106104641.png]]
- Metodo di `poincare`
I `punti singolari di un impronta` possono essere individuati controllando il valore dell'indice di poincare, calcolato in ogni punto i, j dell'immagine lungo una curva di Np punti. In particolare per l'indice :
- indice = ½ ----> Core
- indice = ½ ----> Delta

Teta è il campo di orientamento
X(k) e Y(k) sono le coordinate del k-esimo punto della curva.