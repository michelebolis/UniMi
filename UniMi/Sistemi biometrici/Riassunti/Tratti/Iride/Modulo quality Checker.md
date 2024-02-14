Modulo quality Checker
La probabilità di avere una iride già a fuoco è tutta via molto bassa perché :
- L'ingrandimento del sistema ottico è molto spinto
- L'occhio si muove rapidamente eseguendo spesso micro-movimenti non controllabili.
- L'illuminazione è limitata ( non possiamo usare lampade con troppi watt, altrimenti accecheremo l'utente che si vuole identificare).

Per poter avere un tempo di integrazione breve, occorre fare entrare molta luce nell'obbiettivo, ma questo implica una focale non adatta a riprendere bene a fuoco l'iride. Il fuoco dell'iride viene quindi controllato con dei filtri via software :

L'effetto di sfocatura di una immagine dovuto ad un sistema ottico può essere parzialmente riconvertito applicando un filtro di deblur, esso si comporta al contrario rispetto alla parte del sistema ottico che produce la sfocatura. 

Il filtro di deblur tende ad aumentare le frequenze alte dell'immagine che erano state attenuate dal blur. La maschera del filtro (kernel) è caratterizzata da una matrice 8 * 8. 
Il controllo impiega circa 15 ms, può essere eseguito a livello di frame.

Se l'immagine dell'iride acquisita è troppo mossa occore scartarla in quanto l'iris code risultante sarebbe composto solo da bit casuali dipendenti dal rumore del CCD. Se fosse eseguito un enroll con un immagine di bassa qualità, si avrebbe quasi sicuramene un false-not match.

A differenza delle impronte digitali, non si usano particolari pre-filtraggi nel caso dell'iride:
- In alcuni casi si applica un contrast stretching per migliorare il contrasto e quindi la intellegibilità della immagine da parte degli operatori. Tuttavia questa operazione non modifica sostanzialmente il funzionamento complessivo del sistema.