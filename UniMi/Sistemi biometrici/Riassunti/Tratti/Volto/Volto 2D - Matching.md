Nella fase di `enroll` a partire dai volti si calcolano le `autofacce con la tecnica della PCA`.
`Verification`: `ogni volto del DB può essere riscostruito come una combinazione lineare delle autofacce`. Se un nuovo volto viene ricostruito male, allora :
- Non è un volto
- È un impostore

Analisi locale
Lavorano invece sul riconoscimento, misurazione e confronto dei dettagli del volto:
- Misurazione del naso
- Della bocca
- Occhi
- Valori ritornati da particolari funzioni di trasformazione ( gabor wavelet)

Model based
I modelli model based, non estraggono una feature singola, ma `adattano un modello sulla faccia`, ne trovano i coefficenti e vanno a confrontarli con quelli delle facce usare in enrollment
![[Pasted image 20231115095733.png]]
Rientrano nella categoria dei `metodi graph matching`, in questi modello il volto è rappresentano come una `rete di nodi / feature vectors` sui punti peculiari del volto. Trovato attraverso gabor welvet con diverso orientamento e scala.
![[Pasted image 20231115095746.png]]
`Servono almeno due immagini per trovare il modello del volto` (grafo).
La comparazione di due facce è eseguita misurando quanto sforzo è necessario per adattare un grafo tirando i nodi.