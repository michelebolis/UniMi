Obiettivi:
- `Migliorare la chiarezza della struttura dei ridge` nelle regioni dove è possibile
- `Marcare le regioni dove non è possibile estrarre un informazione` perché è presente troppo rumore

`In entrata avremo quindi un immagine a toni di grigio, in uscita un immagine a toni di grigio o binarizzata a seconda dell'algo utilizzato`.

Come è possibile raggiungere tali obiettivi :
Per ottenere i massimi risultati nell'evidenziare la struttura dei ridge in un immagine occorre 
- `Filtri contestuali`
Questa categoria di filtraggi per le immagini `modifica automaticamente i propri parametri per meglio adattarsi al mutare delle condizioni delle immagine`, i parametri presi in considerazione sono :
- `Distanza` fra i ridge media, la quale è fissa
- `Orientamento` dei ridge, si muovano con una certa linearità
- Livello di rumore presente

Tali filtri si basano sul concetto di convoluzione :
![[Pasted image 20231106104154.png|300]]

L'operazione \* non è una moltiplicazione ma è un operazione di filtraggio :
- Viene costruito un kernell di dimensione 3\*3 più piccolo dell'immagine di partenza. 
- Verrà preso un blocco di dimensione 3\*3 dall'immagine di partenza, dove ogni pixel dell'immagine verrà sovrapposto al kernel. L'immagine di uscita verrà costruito un pixel alla volta.
- Viene moltiplicato pixel \* pixel un singolo pixel dell'immagine con un pixel del kernel. Il pixel dell'immagine di uscita terrò conto di quello che succede nel blocco originale dell'immagine e del contorno del kernel.
- L'elemento centrale del kernell viene piazzato sopra il source pixel. Il source pixel viene rimpiazzato da una somma pesata di se stesso e tutti i pixel vicini.

In uscita avremo un `pixel con un valore alto, quando l'immagine assomiglia al filtro`. Nell'immagine di uscita verranno risaltati le parti dell'immagine che assomigliano al filtro.

I filtri contestuali lavorano sull'immagine in ingresso attraverso un operazione chiamata `convoluzione con una maschera di filtraggio`.
- A seconda del tipo di maschera usata (kernell) `il filtro aumenta/diminuisce alcune caratteristiche piuttosto che altre`
- Una parte del filtro controlla la porzione dell'immagine in esame e adatta i parametri della maschera.

Alcune tipologie di filtri :
- Filtro di `O'Gorman And Nickerson`
La forma particolare di questa maschera è fatta per fare "match" con lo spessore dei ridge, la loro distanza di separazione, il valore massimo e del minimo di un introno del punto di esame

Mediante la `rotazione della maschera` si cerca anche di fare "match" con la direzione preferenziale di ridge. inoltre questo filtro tende ad `attenuare il rumore locale`
![[Pasted image 20231106104255.png]]

- Filtro di `Gabor`
Viene creato il cosi detto `banco dei filtri`, preparato per varie angolazioni e varie distanze inter-ridge. Viene quindi estesa il filtro precedente, con l'idea di utilizzare più dita.

La maschera che offre migliore "match" viene impiegata nella convoluzione di quella zona dell'immagine. 
- Quando si analizzano regioni “unrecovable” il filtro viene disattivato per non creare falsi ridge (artefatti).
-  In alcune regioni, tuttavia degli artefatti possono essere introdotti ugualmente.
-  Il filtraggio di Gabor può introdurre effetti di blocchettizzazione