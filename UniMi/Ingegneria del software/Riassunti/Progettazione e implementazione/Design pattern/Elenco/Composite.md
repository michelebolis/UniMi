Situazione: gestire strutture ad albero per rappresentare gerarchie di parti e insiemi uniformemente 
Scopo: esso mira a gestire oggetti singoli, gruppi e persino gruppi di gruppi in maniera uniforme e trasparente in modo che un client non interessato alla struttura gerarchica possa utilizzarli senza accorgersi delle differenze.

![[Pasted image 20231109094033.png]]

Abbiamo quindi gli oggetti singoli, rappresentati dalla classe _Leaf_, e gli oggetti composti rappresentati dalla classe _Composite_. Per realizzare l’uniformità di gestione dobbiamo introdurre un livello di astrazione, quindi Leaf e Composite implementano una stessa **interfaccia Component** contenente la definizione delle operazioni comuni.  
L’uso dell’interfaccia comune permette di definire all’interno di Composite le operazioni di aggiunta e rimozione di oggetti al gruppo in modo generale, permettendo cioè che un _Composite aggreghi sia Leaf che altri Composite_.

A proposito di tale aggregazione, dallo schema UML possiamo notare le relative cardinalità: “0..n” dal lato del Composite e “0..1” da quello del Component. Esse indicano che:

- Un’istanza di Composite aggrega 0 più istanze di Component al suo interno: in questo modo si permette che al momento della creazione il Composite sia totalmente vuoto; se questo non ha alcun senso logico nell’applicazione si può invece modificare la cardinalità in “1..n” imponendo che al costruttore di Composite venga passato un Component iniziale da contenere;
    
- Un’istanza di Component può essere contenuta in al più un’istanza di Composite: può cioè essere libero o aggregato in un gruppo, ma non può appartenere contemporaneamente a più gruppi, cosa che forza una struttura strettamente ad albero.

Nella maggior parte dei casi un’istanza Composite utilizzerà gli oggetti aggregati per implementare effettivamente i metodi descritti dall’interfaccia comune, delegando a loro l’esecuzione effettiva e limitandosi ad elaborare i risultati. 

Vantaggi: semplice e trasparente perché non si deve preoccupare se sta interagendo con elemento singolo o composito

Un “dialetto” del pattern tenta di risolvere il problema dell’indistinguibilità tra Leaf e Composite introducendo nell’interfaccia Component un metodo `getComposite` che in un Composite restituisca `this` e in una Leaf restituisca `null`. L’uso di valori nulli e la necessità di strani casting rende però pericolosa l’adozione di questa versione del pattern.

Svantaggi: minore possibilità di controllo su che tipo di oggetti si sta interagendo e su che cosa contenga Composite
