Impronte digitali - Rappresentazione
Rappresentazioni delle impronte
La rappresentazione delle impronte digitali in un sistema biometrico dipende dal :
- [[Impronte digitali - Sensori]]
- [[Impronte digitali - Livelli di analisi]]
- `Caratteristiche che si estraggono`:
	- Posizione dei ridge ( orientamento. Forma)
	- Minuzie ( coordinate, orientamento, tipo)
	- Pori (coordinate)

Il sample della impronta è una immagine in toni di grigio quando si controlla :
- Risoluzione
- Bit per pixel

Un esempio : L'FBI digitalizza le impronte del DB nazionale a 100 DPI con 8 bit per pixel. Una cartella con 10 impronte occupa circa 10 MB.

Formati di compressione:
- Usando un `formato "lossless"`, con le impronte si ottiene un `fattore di compressione 2:1`, troppo poco per un archivio di grandi dimensioni. Il formato di compressione è interno a sistema, viene utilizzato per salvare le immagini sul DB al fine di non utilizzare troppo spazio di memorizzazione.
- Esistono dei formati di compressione appositi per le immagini di impronte digitali:
	- L'FBI e il NIST americano usano il seguente algoritmo (WSQ) `Wave scalar Quantization`

Formati di interscambio:
Oltre al formato di rappresentazione interna del templare, nel sistema biometrico ( che può essere privato o segreto essendo del produttore), esistono formati di interscambio dei dati fra istituzioni/aziende
`ISOC/IEC 19794` è un documento ISO che regola i "`biometric interchange formats`"
