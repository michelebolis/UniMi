- test ideale 
- reti di petri di alto livello per il tempo 
- test valido e criterio studiato che seleziona test validi 
- azienda perché dovrebbe scegliere open source 
- copertura comandi vs decisioni 
- beebugging e analisi mutazionale 
- dimostrazione rdp da conservativa a limitata 
- polimorfismo e collegamento dinamico 
- modello a spirale 
- assiomi reti tbn 
- 2 regole xp da consigliare a colleghi 
- relazioni uml tra classi e tra istanze
- UML le varie frecce e esempi 
- vitalità transizioni 
- criterio copertura comandi vs decisioni in particolare un esempio dove vale una e non l'altra
 - Cos'è la verifica e convalida? Perché i requisiti di solito sono meno formali delle specifiche?
- Cos'è SCM? Perché i manufatti sono file di testo di solito?
- Cos'è il TDD?
- Cos'è il refactoring? Chi ha coniato il termine? 
- Come nascono e cosa sono le metodologie Agile? Quali sono i quattro valori del manifesto (e.g. prediligere la collaborazione tra persone)? Dimmi alcuni dei principi (??? non le tecniche dell'XP) (e.g. KISS)?
- A cosa servono le reti di Petri?
- Che cos’è la nullability? Perché è importante? Qual è la caratteristica del valore null che “da fastidio”? 
- Processi, parlami positivamente del modello a cascata. Modelli di ciclo del software (descrittivo). Come nasce il modello a cascata? 
- Terminologia di base di verifica e convalida. Sbaglio, errore, difetto, anomalia…, esempio in cui si presenta anomalia ma non (difetto o errore (?)) 
- Prova a scrivermi la relazione di conflitto, relazione di concorrenza (fai esempi e scrivi in maniera formale) evidenzia strutturale/effettivo 
- Mi parli di criterio di selezione. Che cos’è? Perché dobbiamo scegliere nei test un sottoinsieme del loro domino (cioè non seleziono tutti i test, ma solo alcuni)? Divagato su definizione di criterio valido. La parola criterio l’abbiamo usata in altri contesti, quali? Criteri di copertura dei comandi/decisioni ecc. dimmi qualcosa su uno di questi. Esempio dove “un criterio è soddisfatto e l’altro no” 
- Da dove derivano, chi è che le scrive le specifiche? Dopo averle raccolte cosa devi fare prima di implementarle?
- Pattern, chain of responsability, interface segregation 
- Modelli iterativi e modelli sequenziali, prototipale (?) 
- boh... di una transizione. È una caratteristica strutturale? 
- Che è il TDD, come funziona? È una tecnica di specifica?
- Esempio di rete limitata. 
- Differenza tra merge e pull request.
- Testing funzionale
- Cosa sono gli STUB? Quando devo “mockare”? Perché non voglio usare le altre classi già presenti? Quando invece NON POSSO usare le altre classi? Problemi uso mock (ad esempio di performance, perché non simula reale tempo di risposta). Dumming/stubbing. Che funzioni usi per fare stubbing con mockito? 
- Albero di raggiungibilità vs albero di copertura. Cosa rappresenta Ω? Vari esempi 
- definizione e struttura di una rete 
- perché abbiamo studiato le reti di Petri? 
- quando una transizione si dice viva? Definire la vitalità e i gradi 
- definizioni di: raggiungibilità, sequenza, conflitto e concorrenza a volte anche chiede anche di rappresentarle graficamente 
- conservatività e limitatezza: quali sono le differenze tra queste due proprietà? Enunciarle e poi rappresentare una rete limitata ma non conservativa 
- analisi statica e dinamica delle reti di Petri

2024
Orale 1
- Errore "con cui ti boccerebbe santini": gestione nullability
- Parlami della Nullability -> 
	- Per i parametri: contratto (asserzioni) o programmazione difensiva  
	- Valori di ritorno: 
		- NullObject (vantaggio: semplifica i controlli, in particolare se sul ritorno devo usare i metodi della classe ritornata)
		- Tipi opzionali: wrapper che mi permette di sapere se c è o meno
- Differenza tra modelli sequenziali/iterativi/incrementali (descrittivi vs prescrittivi). ATT gli incrementali IN AGGIUNTA (NON A DIFFERENZA) degli iterativi hanno la consegna come fase
	- Differenza anche il modello prototipale (pubblico: faccio vedere al cliente le funzionalità esterne del prototipo). COME DETTO A LEZIONE è iterativo e non incrementale in quanto il prototipo non viene consegnato ma buttato 
- Mi parli dell'Analisi Data Flow e scelga un criterio
	- MONGA INTERVIENE
	- NON dire ci sono 3 cose ma poi me ne ricordo 2
	- regole del data flow
	- criterio di copertura delle definizioni (vuole davvero la definizione matematica) 
		- relazione con il criterio delle decisioni: decisioni non include definizioni MA NEACHE viceversa (es con un ciclo in cui ho bisogno di 2 iterazioni). In realta perche esaminano due cose diverse
- Rete di petri: conservativita rispetto a una funzione 
	- Legame con la limitatezza: una rete conservativa è limitata ma non viceversa (con esempi, serve una rete con 2 transizioni e 2 posti)

Orale 2
- pattern adapter
	- UML class: frecce significato e NOME: generalizzazione (linea tratteggiata e triangolo bianco) e implementazione (linea continua e triangolo bianco)
		- composizione (quella "nera"), aggregazione (quella "bianca"), dipendenza (linea "tratteggiata": parte del codice dell'interfaccia viene usato)
	- protected = package + quelli che eredito da te
	- codice legacy: quale scelgo tra class e object adapter?
		- class adapter perche riesco ad avere un oggetto che puo essere visto come nuovo (perche implementa l interfaccia) e vecchio (perche estende la classe vecchia)
- cosa perdo da albero di raggiubilita a albero di copertura 
	- copre != copribile

Orale 3
- Interfacce: non devo avere interfacce che sappiano fare tante cose
	- posso fare un metodo che non ritorna niente anche se dovrei se c è un eccezione
	- come fa un interfaccia a dipendere da una classe? se è presente nella segnatura dei metodi --> violo dependency inversion
	- in java moderno posso impedire che venga estesa
- nel testing, bisognava usare le interfacce invece nelle classi concrete. Cos è il mocking
	- fake object non è fattibile in mockito
- sei appena stata assunta, Mattia è il tuo manager, convincilo con 3 tecniche exp con un linguaggio che capisca un manager
	- CI, trovo errori prima e ho una versione presentabili al cliente
- reti di petri: non ho capito a cosa serve l analisi di raggiungibilita, quando è utile?
	- quali sono le informazioni che perdiamo con la copertura? 
		- marcatura raggiungibile
			- Condizione sufficiente: se è presente come nodo nell albero
			- Condizione necessaria: o sono uguali o c è omega MA NON sufficiente perche omega non so quanto è, PERDO infatti la capacita dei numeri che puo rappresentare (omega = numero grande a piacere)

Orale 4: 
- come fare refactoring con pattern notando codice duplicato
	- strategy con UML (FARLO PRECISO)
	- template: SE ho una classe astratta che non implementa per es sort e poi n classi concrete che implementano il sort
- cosa intendiamo per il SW "che funzioni"
	- C è un legame tra affidabilita, robustezza e correttezza
		- affidabilita non implica correttezza 
		- correttezza non implica affidabile in quanto ci potrebbe essere stata un incomprensione nei requisiti
		- cliente preferisce correttezza o affidabile? Forse meglio affidabilita cosi faccio contento il cliente ma ci sono dei rischi legali
- secondo e terzo grado di vitalità di una transizione (esempio)

Orale 5:
- 