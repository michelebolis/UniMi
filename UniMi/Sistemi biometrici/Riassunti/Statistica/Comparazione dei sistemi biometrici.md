La comparazione dei sistemi biometrici, avviene `comparando i valori degli indici` di merito viste nelle lezioni precedenti:
- Numeri puri come EER, FTM; FNTM; FAR. Meglio se espresse rispetto alla soglia T del sistema biometrico.
- Descrittive:
	- `Distribuzione dei genuini` $pn(t)$
	- `Distribuzione degli impostori` $pm(t)$
- `La comparazione maggiormente efficace è quella che si può avere confrontando le curve DET/ROC dei due sistemi in merito`.

1. `Comparazione con DET`
`Non sempre la comparazione basato su EER è adatta`. 
`Bisogna scegliere la regione di funzionamento del sistema in termini di FNMR e FMR` e successivamente confrontare i sistemi in quelle due zone della curva, per vedere quale sistema si comporta meglio.

Deve essere richiesto al committente un grado di FNMR e FMR, nel quale l'applicazione deve lavorare.

`Errore zero sempre impossibile nella pratica`

![[Pasted image 20240214093256.png|300]]

2. `Comparazione con CMC`
La curva rappresenta la `probabilità di identificare una persona in base al pool di impronte` che abbiamo selezionato. Le impronte nel pool sono ordinate in base al match score.
`Si usano solo gli score`, non si usa nessuna soglia.

![[Pasted image 20240214093309.png|300]]
La curva CMC non è derivabile da altri plot

Distribuzioni molto ben separate ( fra genuini e impostori) produrranno poi una buona curva DET e ROC e CMC.

`Buona ROC non è detto buona CMC`: `Diverse CMC possono avere la stessa ROC`

![[Pasted image 20240214093319.png|300]]

La distribuzione individuale dice se mi comporto bene verso me stesso e verso gli altri.

`Ogni identità contribuisce in maniera unica alle performance del sistema`, ovvero le statistiche aggregate DET/ROC non predicono bene le statistiche rank che dipendono esattamente dagli individui.

3. `Comparazione con distributori genuini e impostori`
Le distribuzione dei match score sono alla base delle curve ROC, CMC, DET.
Sono un `ottimo modo per vedere il comportamento del sistema` e capire se ci sono:
- Asimmetrie
- Code non simmetriche
- outlier

4. `Distribuzioni d'`
`d' è la misura del grado di separazione presente fra le distribuzioni degli impostori e dei genuini, calcolato considerando le loro medie e deviazioni standard` .

Il parametro d' da solo `non è esaustivo`, stesso d' ma DET diverse.

`Possiamo descrivere le regioni di una curva DET nel seguente modo`:
Regioni con `bassi FMR` -> regioni di `security` $1-FAR(t)$
- `Bassa possibilità che un utente non autorizzato possa entrare nel sistema`.
- Tuttavia `la probabilità che un utente autorizzato non riesca ad entrare nel sistema al primo tentativo è più alta`. Occorrerà che l'utente presenti più volte il suo tratto biometrico al sensore.
Regioni con `basso FNMR` -> regioni di `convenience` $1-FRR(t)$
- Un utente autorizzato non perde tempo, in quanto con bassa probabilità non entrerà al primo tentativo
- Tutta via avremo una percentuale più alta di utenti non autorizzati che riescono ad accedere al sistema.