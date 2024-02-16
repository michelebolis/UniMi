Introduzione
Tratto biometrico accettato dagli utenti. Può essere utilizzato in modo continuo ( è uno dei pochi ), mentre continuo a parlare un sensore potrebbe continuare a rilevare il tratto biometrico.

Tuttavia abbiamo una bassa accuratezza ma un moderato costo, è inoltre abbastanza facile da frodare.
Il template deve essere di grandi dimensioni.

La voce è biometrica in quanto ognuno parla nel proprio modo, Ci sono delle differenze fisiche,  ( differenze muscolari tra polmoni, corde vocali, laringe, faringe). C'è inoltre un secondo strato che riguarda il comportamento dell'individuo, differenze corporamentali  ( accento, modo di esprimersi)

[[Voce - Riconoscimento]]
[[Voce - Sensori]]

Caratteristiche generali della voce:
Elaborazione della traccia vocale per estrare i parametri del modello acustico del parlatore ( però dipendente dal linguaggio e dal soggetto) :
- `Anatomia` (dimensioni e conformazione di bocca e gola)
- `Comportamento` (timbro di voce, modo di parlare)
- Solitamente richiede complesse elaborazioni del segnale acustico (analisi di spettro, periodicità)

`Diverse caratteristiche` si possono estrarre dalla voce, da quelle linguistiche fino a quelle acustiche sonore di basso livello:
- `Alto livello`: `caratteristiche lessicali e sintattiche come la co-occorrenza delle parole o dei fonemi`
- `Livello intermedio`: `qualità della voce`
- `Basso livello`: energia del suono nella varie `bande spettrali`

Passi principali effettuati per lo speaker recognition:
- `Pre-filtraggio`
- `Elaborazione delle feature statiche` (MFCC mel-frequency cepstral coefficients) e dinamiche
- `Modellazione del parlatore`
- `Comparazione dei modelli e decisione`
Vantaggi :
- Tecnologia `basata su hardware di larga diffusione`
- Buona accettabilità da parte degli utenti
- Template compatto `50KB - 100KB dimensione sample`
Svantaggi :
- Possibilità di `tempi lunghi di enrollment`
- Elevare dimensioni del templare circa 1MB
- Sensibilità ai rumori di fondo
- `Variabilità intraclasse` dovuta a malattia o condizioni ambientali
- Facilità falsificazione tratto

Applicazioni nel mercato:
Ad oggi è stato stimato che il mercato riguardante il riconoscimento o l'analisi vocale raggiungerà un valore di 28.3 bilioni di dollari nel 2026. 
Le aziende stanno implementando l'autenticazione vocale in praticamente ogni settore (call center, robotica, e-commerce)

Applicazioni attuali:
- Autenticazione degli utenti in applicazioni di medio/bassa sicurezza
- Attività investigative
- Sistemi multimodali

Accuratezza:
`MFCC features = circa 99% di accuratezza`, si tratta delle feature migliori per il riconoscimento della voce.

WER ( accuratezza del riconoscimento della voce) :
Con:
$$1-WER = \frac{S+D+1}{N} = accuracy\% $$
- N = il numero di parole nella reference audio N = S + D + C
- S = il numero di sostituzioni
- D = il numero di cancellazioni
- I =  il numero di intersezioni  
- C = il numero di riconoscimenti corretti

`Ranking error Rank(n)`:  si tratta di un tipo di metrica relativa al problema della identificazione (1:N). `Data un sample in ingresso, vogliamo trovare il template genuino corrispondete tra n individui presenti in un DB`.
Il problema viene risolto `comparando il sample con tutti gli n candidati del DB e scegliendo il candidato a distanza minima` (con maggiore similarità).

`Rank(N) = è il rapporto dei template della query per cui i confronti con i genuini sono tra gli n confronti con i valori di somiglianza più alti nel database`.

Procedimento :
- Prendo 1 template
- Faccio N comparazioni
- Prendo gli n score più simili
- Vi è un genuino Si = 1 , no = 0
- Rifaccio con gli altri utenti e medio il tutto ottengo rank(n)

In un sistema ideale, i valori di matching più alti sono sempre assegnati a delle comparazioni tra genuini. `Nel sistema ideale Rank(1) = 1.0`. Significa che tutte le comparazioni fra genuini hanno ottenuto valori di similarità più alti.

Curva DET per la voce :
![[Pasted image 20240214091428.png|300]]

Il `voip tende a migliorare il FMR` in applicazioni con maggiore reliability e minore sicurezza .
Oltre i 30secondi di enrolment inoltre non si ha alcun miglioramento del tasso di errore in fase di autenticazione o identificazione.

Time Warping = allinea le firme on-line non quelle off-line che sono statiche.