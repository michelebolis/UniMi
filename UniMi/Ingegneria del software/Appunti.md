Carlo Bellettini e Mattia Monga

NON c è un vero libro 

Parti:
- Processi di gestione del SW
- Progettazione del SW
- Verifica e convalida
- Specifiche del SW

Esame
- Lab, 4 ore OPPURE due lab durante l'anno di 4 ore (entrambi sono in coppia casuali)
- Esame orale per la teoria

Storia 
Negli anni 50-60 si è colta la necessità si superare i metodi di produzione artigianali, chi produceva il SW era anche colui che lo doveva utilizzare.

Dobbiamo chiarire e rendere comune un modo di lavorare che ci possa assicurare di produrre SW di qualità. Vengono definite quindi tecniche e ...

## Approccio ingegneristico
- Target: si pone un obiettivo
- Metric: viene definita una metrica per misurare
- Method / process / tool utili per raggiungere il target
- Misuro il lavoro fatto chiedendomi se sono vicino all'obiettivo (non mi interessa l'obiettivo ma se il mio approccio ha funzionato)
	- NO: modifico il processo
	- SI: accetto

Target come
- Riconosciuti i problemi, dobbiamo toglierli
	- Il numero e il tipo di persone coinvolte. Stakeholders diversi (sviluppatore, cliente, manager...)
	- Dimensione del SW: es l'aumento delle persone coinvolte non implica un aumento in modo diretto della velocità di produzione del SW
	- Il SW è SOFT: è malleabile, quindi porta a molteplici versioni ed evoluzioni
- Date certe qualita, vogliamo raggiungerle
	- Utilizzando un buon processo ho un'elevata probabilità di produrre un prodotto di qualità
	- Qualità a cui puntiamo è di interesse per uno stakeholders
		- Funzionamento
			- Correttezza: se requisiti (necessità dell'utente) e specifiche (necessità che io ho compreso di dover fare) coincidono. R.Glass' Law: le mancanze nei requisiti sono la fonte primaria di fallimenti.
			- Affidabilità: l'utente si puo fidare che vengano rispettati i requisiti richiesti
			- Robustezza/Safety: 
		- che sia bello
			- Proprietà esterna: percepibili dal cliente
				- Usabilità: è una fase fondamentale ma costosa e poi non brevettabile. Nielsen-Norman's Law la usabilità è quantificabile.
				- Efficienza nell'uso delle risorse (tempo o spazio): diventa un requisito importante. Soft-realtime: . Ricordando che i tempi di sviluppo sono alti, la velocità dell'HW potrebbe aumentare nel tempo e quindi risolvere in parte i problemi di efficienza.
				- Verificabilità: SW leggibile tanto che sia facilmente verificabile la sua correttezza.
			- Proprietà interna: percepibili solo da chi lo sviluppa
		- che mi faccia diventare ricco
			- Riusabilità dei componenti: alcune volte non è direttamente riutilizzabile ma deve essere adattato. McIlroy's Law SW riuso riduce il tempo e incrementa la produttività e la qualità.
			- Manutenibilità: rende facilmente mantenibile il SW già consegnato
				- Riparabilità: correzione errori
				- Evolvibilità: estensione dei requisiti. M.Lehman's Laws un sistema che è usato cambierà, quindi un sistema in evoluzione aumentera la sua complessità a meno che il lavoro è fatto per ridurne.
				- Perfettivibilità: non cambiando requisiti, posso provare a fare cambiamenti volti a migliorare efficienza o usabilità. Metodo agili: se mi accorgo che nel mio codice si puo fare meglio qualcosa, lo posso lasciare li cambiandolo successivamente MA è come se stipulassi un debito, maturano infatti nel tempo degli "interessi" costandomi in termini di tempo.

Come deve essere un processo: deve funzionare, deve essere bello e deve farmi diventare ricco
- Robustezza: per qualcunque problema sia del processo che esterno ad esso (es personale malato)
- Produttibilità: 
- Tempismo: spesso si privilegia la velocità di arrivare in tempo che la qualità del processo stesso.

---

Si è iniziato a capire che produrre codice non è solo scrivere codice ma bisogna anche:
- risolvere dei problemi di comunicazione 
- essere rigorosi 
	- Ipotesi di Bauer Zemanek: metodi formali riducono significamente gli errori di design o li eliminano anticipatamente; per essere realistici non sempre possiamo lavorare con metodi formali).
- considerare che ci sono diversi aspetti da considerare in diversi momenti dello sviluppo

modellare ciclo di vita del SW
- identificare i vari passi e le attività chiedendosi
	- cosa bisogna fare e fino a quando
	- chi lo debba fare

Fasi
## Studio di fattibilità 
Consiste nella 
- Definizione preliminare del problema considerando il possibile mercato e i concorrenti.
- Studio dei diversi scenari di realizzazione sia architetturale, HW, di personale, scegliendo se produrlo internamente o subappaltandolo
- Stima dei costi, dei tempi di sviluppo, delle risorse necessarie e dei benefici delle varie soluzioni
Spesso questa fase di analisi si effettua in modo esterno per non sprecare risorse, per avere una visione esperta dando dei limiti temporali e di costi

Possibili output: un documento spesso in linguaggio naturale

## Analisi e specifica dei requisiti
- Comprendere il dominio applicativo
- Identificare gli stakeholders 
- Capire le funzionalità richieste: capire solo $cosa$ deve fare il sistema $non$ $come$ (è una fase piu avanti, quella di progettazione). 
	- Metodi esaustivi: in un linguaggio naturale 
	- Metodi operazionali: modello eseguibile in qualche forma che fa vedere le caratteristiche che il modello deve rispettare
- Dobbiamo considerare solo il prodotto dal punto di vista dell'utente, non gli interessa il progetto o l implementazione, ma quello che deve fare il sistema considerandone
	- Correttezza
	- Verificabilità: da linguaggio formale 

Possibili output:
- Documenti di specifica
	- Documento contrattuale approvato dal committente
	- Una base per il lavoro di design e di verifica
	Risulta quindi importante avere un documento formale
- Manuale utente o maschere di interazione desiderate (la vista esterna per eccellenza)
- Piano dei testi di sistema: collaudi che certificano la correttezza
David Law: il valore dei modelli dipende dalla vista adottata ma nessuna è migliore per tutti gli scopi


## Progettazione
Considerando le specifiche fissate, definiamo ora l'architettura del sistema in particolare
- scelta di una architettura SW di riferimento
- Scomposizione in moduli o oggetti
- Identificazioni di patterns

Possibili output:
- Documento di specifica di progetti considerando diversi linguaggi

## Programmazione e test di unità
Le black box definite al punto precedente vengono realizzate
Lo sviluppatore deve avere testato i suoi moduli in modo indipendente utilizzando framework per il test (che ovviamente non consegnerò all'utente)
- moduli stub/fittizzi (fittizzio cioe che in apparenza fa quello che dovrebbe fare in modo sicuro e semplice): moduli che la mia classe utilizza
- moduli driver: moduli che usano la mia classe 

Possibili output:
- insieme di moduli sviluppati separatamente con un interfaccia concordata e singolarmente verificati

## Integrazione e test di sistema
Ora è necessario unire i vari componenti realizzati
- Test di integrazione: consideriamo un sottoinsieme dell'applicazione alla volta, sostituendo a mano i moduli di testing con i moduli reali
	- top-down
	- bottom-up

## Manutenzione
- Correttiva 
- Adattiva 
- Perfettiva

Output: un prodotto migliore

Altre attività:
- Documentazione : può essere vista come attività trasversale o posteriore
- Verifica e controllo qualità (QA quality assurance)
- Gestione del processo, in particolare degli incentivi, responsabilità, eccezioni
- Gestione delle configurazioni, cioè delle relazioni inter-progettuali


## Modelli di ciclo di vita del SW
Modelli
- prescrittivi: da un modo per procedere, quella giusta (spesso in realtà incompleti)
- descrittivi: rappresentano una situazione prendendone solo alcuni aspetti perche non direttamente utilizzabili 

Modelli
- incrementale: quando nelle iterazioni viene inclusa la consegna. Quello che viene fatto dopo la consegna fa parte del processo
- iterativi

es 
- implementazione iterativa: stressa la modularizzazione e l'identificazione di sottosistemi e si ripetono fasi di coding ed integrazione
- sviluppo incrementale
	- viene esteso a tutte le fasi, specifiche comprese
	- la fase di manutenzione in senso stretto sparisce diventando semplice riciclo


Problemi con i modelli incrementali
- il lavoro di planning viene complicato in quanto lo stato del processo è meno visibile e bisogna pianificare tutte le iterazioni
- si riconosce che bisogna rimettere mano a ciò che si è fatto MA il sistema potrebbe non convergere, non arrivando mai a un risultato che consegno e che non lo tocco piu
- cosa è un iterazione e quanto dura?
	- rischio di voler mettere troppo nella prima iterazione
	- rischio di overhead dovuto a troppe iterazioni
	- rischio di avere un eccessivo overlapping tra le iterazioni in quanto non si hanno feedback dell'utente

- ### Modello a cascata/document driven
Ogni fase produce un semilavorato che è utilizzato dalla fase successiva senza possibilità di retroazione. Forza quindi una progressione lineare.
Nasce durante la fine degli anni 50 in un progetto militare

Vantaggi:
- Garantisce una buona separazione dei compiti
- è possibile pianificare i tempi e monitorare lo stato di avanzamento, ma è a senso unico

Svantaggi:
- La manutenzione avviene post rilascio perché non è prevista retroazione (non si possono fare modifiche a specifiche, codice, documentazione...), ed anzi è considerata un'eccezione. 
	Tuttavia il 70% dei costi di sviluppo ricadono in questa fase 
- Rigidità 
- Congelamento sotto prodotti, essendo vincolati a stime fatte nelle prime fasi
- Monoliticità in quanto la pianificazione è orientata ad un singolo rilascio e la manutenzione è fatta solo sul codice 

- ### Modello a V: 
E' un modello simile a quello a cascata ma espande la fase di testing e chiarisce alcune relazioni. 
Dopo ogni fase si considera la coerenza con le specifiche del progetto.

- ### Modello a cascata con singola retroazione 
Permette una singola retroazione alla fase precedente eventualmente iterabile e ripetibile

- ### Modello ciclo di vita a fontana
In questo modello la retroazione non va alla fase precedente ma sempre al punto di partenza, senza buttare quanto fatto 
In ogni retroazione non è noto a priori la profonda di ogni zampillo. 
E' quindi un modello incrementale 

- ### Modelli prototipali
Considera un prototipo usa e getta
I prototipi possono essere:
- pubblici/esterni: viene presentato al cliente per verificare di aver capito i requisiti e far compiere scelte all'utente
- privati/interni: per esplorare nuovi strumenti, linguaggi, diverse scelte per problemi difficili
Boehm Law: la protopizzazione diminuisce significativamente gli errori di progettazione e raccolta dei requisiti soprattutto per l'interfacce utente

E' un modello iterativo perché il prototipo non glielo lascio davvero (non è incrementale perché non parto da quello)

- ### Modello Pinball Life-Cycle (Ambler)
Il controllo che ho su cosa succede dopo ogni fase è limitato
E' una visione pessimistica di un processo indefinito in cui qualunque passo è possibile e quindi non è misurabile neanche in termini di vincoli temporali

- ### Modelli trasformazionali
Vediamo lo sviluppo del SW come un raffinamento di rappresentazioni formali del problema.
Ad ogni passo vengono specializzate, ottimizzate e rese piu concrete attraverso trasformazioni automatiche o controllate. 

A partire da specifiche formali si ottiene un prototipo che
- differisce dal prodotto finale per efficienza e completezza
- comprende passi di trasformazioni formalmente dimostrabili come corretti, in particolare che portano ad avere la versione finale e che mantengano le stesse qualità precedentemente ottenute

- ### Meta-Modello a spirale
E' un metamodello in quanto si usa per descrive altri modelli
E' guidato dall'analisi dei rischi
Fasi
- Determinazioni obiettivi, alternative e vincoli
- Valutazione alternative, identificazione rischi
- Sviluppo e verifica
- Pianificazione fase successiva
Ad ogni passo mi chiedo se valga la pena continuare, considerando appunti i rischi.

- ### Modello spirale win-win
Evidenzia che le comunicazioni con i clienti e non sono di tipo pacifico ma anzi necessitano di contrattazioni e negoziazione
Questo modello esplicita quindi il rischio di comunicazione


- ### Modello COTS Component Off The Shelf
Prende a principio la riusabilità dei componenti sul mercato di moduli preesistenti, partendo da quelli e attuando un'integrazione

Questa metodologia porta a nuovi problemi quali la classificazione dei moduli e il retrieval dei moduli
Servono degli adattatori per far convivere componenti nati con assunzioni diverse (parametri diversi).
Rischio di importare codice inutile


- ### Metodologie agili: eXtreme Programming
Principi
- Valorizzare gli individui, responsabilizzare gli individui e il team, senza imporre decisioni e deadline dall'alto 
- Valorizzare un SW che funziona piuttosto che una documentazione esaustiva
- Collaborazione del cliente come se fosse nel team
- Capacita di rispondere ai cambiamenti piuttosto che seguire il piano predisposto

---

Bertrand Meyer analizza in maniera critica molti concetti metodologici su come si fa a parlare di un processo.
Lean SW: nasce nella Toyota che punta a ridurre la spazzatura ("waste"), cioè lato SW quello che non interessa all'utente ma anche a livello strutturale.
Si cerca di fidelizzare lo sviluppatore

- Kanban
Si fa una schema a colonne con uno stato di avanzamento nel tempo
Per "Done" si intende fatta, testata E accettata dal cliente
Obiettivo: minimizzare il lavoro in esecuzione, togliere l overhead di content switching
Se sono bloccato su un task e non posso fare altro, non mi devo fermare, ma andare a supportare il collega che sta facendo il componente che mi serve per continuare

- Scrum ("mischia")
L'intero team si concentra su un obiettivo comune chiaro in un breve tempo, bloccando i requisiti del cliente.
Si arriva ad una win-win condition: io lavoro alle richieste mentre il cliente intanto pensa ad altri requisiti

- Crystal
Comunicazione osmotica (spesso assunto nei metodi agili): il team è un concetto reale, un'entita con una conoscenza, quella del team; il codice è del team, non del singolo che lo ha scritto.
MA ciò può funzionare su un team piccolo (potrei dividere il mio team in team piu piccolo applicando metodi agili)


- eXtreme Programming
Incrementa poi semplifica, rendendo il codice piu leggibile, migliore (refactoring)
Nella semplificazione le funzionalità rimangono uguali migliorando le proprietà interne del componente

- TDD Test Driven Development
è una tecnica di progettazione che guida verso il design piu semplice: Red-Green-Refactor
Nonostante ci sia scritto Test, in realtà è un attività di design
Preparando il test, sto scrivendo una specifica, ciò che deve fare il codice, e mi sto mettendo nei panni dell'utilizzatore del metodo.
Passi:
- Scrivi un test che fallisce
- Qual è la piu rapida ottimizzazione che mi permetta di ottenere il Green? Ottengo un test che passa
- Refactor, attività di design pura
TDD = test-first + baby steps

Partire con un test è in realtà pericoloso perché ci si basa unicamente su di esso in quanto non sappiamo se sia un rappresentante abbastanza generico

L'obiettivo è avere il prima possibile un feedback rapido: ripeto il TDD ogni 2-10 minuti


eXP variabili in gioco
- La portata: la quantità di funzionalità che si vogliono implementare
	- è delicata perché la fonte delle funzionalità è l'utente, i cui desideri sono mutevoli
- Il tempo che si può dedicare al progetto
- La qualità del progetto che si deve ottenere (correttezza e manutenibilità). MA questa dimensione si considera non trattabile, deve sempre essere al 100%
- Il costo in termine di risorse finanziarie si possono impiegare per il progetto
Queste non sono variabili indipendenti 
Il cliente mi comunica portata e tempo, e io per avere la qualità massima gli comunico il costo necessario. MA abbiamo detto che la portata è variabile.
Non viene venduto il prodotto MA il tempo, garantendo che io stia lavorando al meglio

principi: confronto
XP 
 - feedback rapido
 - presupporre la semplicità, attuale (contrapposta al design for change)
 - accettare il cambiamento (ma non è il primo obiettivo)
 - modifiche incrementali previste nel TDD
 - lavoro di qualita (voglio che il prodotto sia buono ma anche lavoro in un ambiente di qualita)
Ing SW classica
 - separazione degli interessi (aspects o concerns)
 - astrazione e modularità
 - design for change: anticipazione del cambiamento 
 - generalita
 - incrementalita
 - rigore e formalità

XP ha trovato un buon mix
XP sembra dire di non pianificare per il futuro. XP sostiene che se utilizzi OO e semplicità, il costo delle modifche non aumenta cosi tanto nel tempo
Boehm basandosi sullo studi di casi reali ipotizza una curva di tipo esponenziale per il costo di modifiche. Il costo delle modifiche in un tempo avanzato (debito tecnico) è esponenziale

figure in gioco e responsabilità (in XP)
- Manager e/o cliente: 
	- responsabilità di decidere
		- la portata del progetti
		- la priorita (business value) tra le funzionalità
		- date dei rilasci
	 - diritto di
		 - sapere cosa puo essere fatto con quali tempi e quali costi
		 - vedere progressi nel sistema provati dal superamento di test da lui definiti
		 - cambiare idea, sostituire funzionalità e cambiare priorita
- Lo sviluppatore 
	- ha la responsabilità di decidere
		- Le stime dei tempi per le singole funzionalità
		- conseguenze di scelte tecnologiche e segnalare i possibili problemi tecnici
		- pianificazione dettagliata (ogni 2-3 settimane decidono cosa fare ogni giorno)
	- ha diritto di
		- sapere cosa è necessario fare attraverso dei requisiti chiari attraverso scenari d uso, ognuno con la propria priorita
		- cambiare stime dei tempi secondo la propria esperienza
		- identificare e indicare le funzionalità pericolose
		- produrre SW di qualità 
- Ad ogni iterazione viene definito un tracker, di controllo e stimolo

Approccio di XP: definizione di 12 pratiche che hanno influenze positive o negative tra di loro
1. Planning game: avviene all'inizio di ogni iterazione. Basato sulle storie scritte dall'utente (versione semplificata degli Use Cases di UML). Vengono determinate le funzionalità del prossimo rilascio combinando priorità commerciali e valutazioni tecniche

	Il cliente prepara delle carte con delle frasi brevi di descrizione, caso di test che funge da test di accettazione e il valore di business che ha per lui. Gli sviluppatori (team) invece  stimeranno il tempo necessario. Il manager sulla base delle informazioni sulla scheda, la implementerà alla prossima interazione 
	- Come si effettua una stima da parte del team
		- Ci sono diverse stime possibili ore vs giorni
		- La stima è effettuata dal team, e non dal singolo dev perché risulta piu difficile che qualcosa sfugga all'intero team piuttosto che al singolo, ho una stima piu accurata
		- In realta la ragione è che la stima deve essere del team, deve appartenere al team
		- Problemi
			- Richiede molto tempo, dovremo minimizzare le discussioni
			- Effetto ancora / ancoraggio: il primo che comunica la propria stima, induce negli altri un confronto con essa (da assoluto a relativo). Dovremo minimizzare questo effetto
		Stime agili:
	- Planning poker: 
	1. vengono presentate brevemente le carte con dei numeri che seguono una determinata scala (non lineare o qualitative). Il team può fare domande, richiedere chiarimenti e discutere per chiarire assunzioni e rischi. 
	2. Ognuno sceglie una carta senza farla vedere e si scopre la stima. In questo modo abbiamo minimizzato l'effetto mentre per minimizzare la discussione può parlare solo la carta piu basse e piu alta. SE ci sono tante carte ?, si divide la carte in piu carte semplici
	3. Si vota nuovamente ed è dimostrato che si convergerà piu velocemente all'unanimità. Funziona perché le carte sono molto distanziate e l'unita di misura non è reale ma piuttosto ore ideali (si usano anche i pomodori come unita di misura). 

	- Team Estimation Game Si sfrutta una valutazione comparativa rispetto alla carta precedente, quindi rispetto alla stima del team non alla mia. 
		Prima fase: valutazione comparativa
	1. Ogni dev si mette in fila e si pongono le carte in pila 
	2. Ogni developer svela una carta, la legge, e la pone a sinistra se è piu facile di quella sul tavolo o a destra se è piu difficile o sotto se è equivalente. 
	3. SE il prossimo dev non è d'accordo con l ordine delle carte sul tavolo, muovo le carte spiegando al team la propria motivazione. 
		Pericolo dell'effetto ancora ma attenuato dal fatto che non c è un valore assoluto. 
		Seconda fase: quantificare le distanze
	1. Ci si mette di nuovo in fila utilizzando con carte del planning poker, posizionando la carta piu bassa nella prima colonna 
	2. Il prossimo dev prende il valore successivo e lo posiziona su un ulteriore colonna oppure può spostare una carta valore precedentemente posizionata motivando tale scelta 
		Una volta definito un ordine, cioè quando non ci sono piu carte e nessun dev vuole spostare una carta, sposto le colonne senza una carta sopra, assimilandole alla loro sinistra
		Terza fase: scala assoluta
		Si stima il tempo in ore di una delle carte piu semplici e si calcolano le altre come proporzione rispetto alla prima
		
		Risulta essere un metodo piu veloce se ho molte carte

Velocity: capacità osservata di completare lavori da parte del team. Cio ci permette ad una nuova iterazione di sviluppare tanti punti quanti ne ha fatti all iterazione precedente, compensando stime sbagliate all'interno del team
Tuttavia:
- NON deve essere usato come metro di valutazione tra team o nel tempo
- NON si devono considerare storie non finite
- NON deve essere imposta

---

Probabilmente non serve mappare in ore reali, basta guardare l iterazione prima 
...
è necessario un progresso continuo grazie ad uno scheduling realistico

2. Brevi cicli di rilascio
	Per ridurre i rischi, la vita e lo sviluppo dell'applicazione sono scanditi rilasci di versione del prodotto funzionanti.
	Ovviamente tali rilasci devono essere comunque significativi.
3. Utilizzare una metafora
	Obiettivo: fornire un nuovo vocabolario comune per comunicare con l'utente, permettendo di far comprendere gli elementi fondamentali e le loro relazioni
	Permette inoltre di fornire nuovi elementi di discussione e si sostituisce all'architettura del sistema.
4. Semplicità di progetto
	Massimizzare il lavoro non fatto consegnando le cose utili
	- One and once only: consegnare tutto e solo quello che serve senza duplicazioni
	- KISS Keep It Simple Stupid
	Questo va in contrapposizione con il Design for change 
5. Testing: 
	TDD
	I clienti scrivono i test funzionali per aumentare la loro fiducia, ma la correttezza dei test non può dimostrare la correttezza certa di un programma.
	Ciò facilita il refactoring in quanto si ha confidenza nelle modifiche che vengono apportate.
6. Refactoring: 
	Modifica al codice che NON modifica le funzionalità ma che puntano alla semplicità del progetto. 
	Il refactoring deve essere fatto gradualmente 
	es Tool di coverage per eliminare parti di codice inutile per i test attuali o per aggiungere un test che passi per quelle righe.
7. Programmazione a coppie
	Aiuta ad avere un controllo continuo del rispetto delle regole di XP
	Aiuta l'inserimento di nuovo personale e la sua formazione
	Aiuta a ottenere la proprietà collettiva, la conoscenza osmotica del team
	Aiuta il refactoring in quanto mentre uno scrive codice, il compagno puo pensare a come semplificarlo.
	Dati alcuni test, si è provato che una dimezzamento del personale ha una diminuzione del 25% della produttività in righe di codice, ma questa è una produttività istantanea
	Anche se non ci fossero problemi, il lavoro fatto non viene congelato ma ha una sua vita successiva, correggendolo, ampliandolo. Bisognerebbe quindi usare un arco temporale piu ampio, notando un minore ritorno sul lavoro consegnato
	Lavorare in coppie non è ispezione del codice (leggendo il codice si cercano errori) ma chi non sta scrivendo fa una prima fase embrionale di analisi 
	(I commenti si scrivono per poi rimuoverli, se ho dovuto scrivere un commento non ho scritto codice leggibile )
8. Proprietà collettiva 
	Il codice non appartiene ad una persona sola ma non è neanche senza proprietà, dove tutti possono modificare tutto senza preoccupazioni
	Ci si deve sentire responsabilizzati sull'intero codice anche se non si conosce tutto alla stessa maniera
9. Integrazione continua 
	Nell'ottica di avere feedback rapidi, l'integrazione va fatta piu volte al giorno 
	La coppia, dopo avere risolto il suo problema in piccolo, è responsabile di risolvere anche i problemi di integrazione. L'azione nonostante sia frequente, è rapida perché nel frattempo il sistema non è cambiato molto. 
	Parallelizziamo lo sviluppo e serializziamo l'integrazione. 
	L'integrazione è aiutata molto dai tool di versioning. 
10. Settimana di 40 ore
	Cerca di risolvere 
	- Problema di freschezza del team
	- soddisfazione di lavorare nel team
	- meno problemi familiari
	- minor probabilità di perdere dipendenti e know-how
11. Cliente sul posto
	Coinvolgendo il cliente, la fase di specifica diventa piu leggera perché le scelte/test vengono forniti in tempo reale. 
	Il problema sarà quanto questa figura sia rappresentativa di tutti gli stakeholders
12. Standard di codifica
	Enfatizza la comunicazione attraverso il codice in particolare l'aiuta il refactoring, la programmazione a coppie e la proprietà collettiva 
13. Just rules: 
	Tutti i punti precedenti sono solo regole che il team può modificare o applicarne solo un sottoinsieme

Raggruppiamo per fasi
- Requirements
	- Gli utenti fanno parte del team di sviluppo
	- Consegne incrementali e pianificazioni continue
- Code
	- Programmazione a coppie
	- Proprieta collettiva 
	- Integrazioni continue 
	- Standard di codifica 
- Design
	- Una metafora come visione unificante di un progetto
	- Refactoring
	- Presumere la semplicità
- Test
	- testing di unita continuo
	- test funzionale scritto dagli utenti 

La documentazione in senso stretto non c'è ma è 
- sul retro delle stories
- nel codice tramite standard di codifica che permettono una maggiore leggibilità e soprattutto nei test di utilità
- nelle persone, sia nel cliente che nel compagno di pair programming
La documentazione in exp diventa quindi un sottoprodotto


Quando non si può usare XP
- in ambienti che proibiscono l'uso anche solo di uno degli approcci citati, impossibilità causata da
	- Barriere tecnologiche che impediscono di testare ed avere un feedback in breve tempo, non ottenendo così il feedback rapido
	- Barriere di tipo manageriali o burocratiche 
		- team troppo numeroso o necessità di documentazione di certificazioni basati su di essa 
		- Troppi stakeholders, quindi non riesco ad avere un cliente sul posto rappresentativo
	- Barriere di tipo fisico e logistico
		- Sistemazione degli spazi di lavoro che non permettono flessibilità nella formazione delle coppie di lavoro

Critiche
- Sottovalutazione up-front: cioè di tutto ciò che viene fatto prima di lavorare 
- Sopravvalutazione User stories
- Mancata evidenziazione delle dipendenze tra user stories: sull'ordine e la complessita di sviluppo
- TDD puo portare a visione troppa ridotta
- Cross functional teams: difficile trovare dei team general purpose 


Mesi/uomo: produttività, stime, costi, velocità
mesi/uomo: il prodotto di questi due fattori ci da una costante, la fatica.
All'aumentare delle persone non diminuisco tanto i mesi, perché aumenta la comunicazione necessaria nell'organizzazione (es sarà necessario formarle, alcuni task invece non sono parallelizzabili)
Nella realtà sopra un certo n di persone, il tempo richiesto aumenta. 
Il dimensionamento del team diventa quindi importante 

SE la situazione peggiora in termini di ritardo: 
- prendo conto del ritardo facendo una nuova stima
- diminuisco la portata (diminuisco le funzionalità da realizzare) 
- diminuisco il testing


Open source 
- Cattedrale e Bazaar
1. Raymond: "Ogni buon lavoro SW inizia dalla frenesia personale di uno sviluppatore" 
2. Chiede ad amici o colleghi cosa sanno sull'argomento: nessuno ha una soluzione ma alcuni hanno lo stesso problema o problemi simili
3. Le persone interessate cominciano a scambiarsi pareri e conoscenze sull'argomento
4. Le persone interessate che intendono spendere delle risorse sulla soluzione del problema danno il via ad un progetto informale 
5. I membri del progetto lavorano al problema finche non raggiungono dei risultati presentabili (qui diventano open source)
6. Si rende noto il lavoro svolto e arrivano i primi suggerimenti esterni. E' utile che ci siano errori perché può invogliare altra gente a partecipare
7. Iterazione tra vecchi e nuovi membri del gruppo
8. Nuove informazioni vengono acquisite e ritorna al punto 5


Alcune frasi
- "Se dai a tutti il codice sorgente, ognuno di essi diventa un tuo ingegnere"
- "Se ci sono abbastanza occhi, gli errori diventano di poco conto", il SW open source si dice essere piu sicuro 
- "Se tratti i tuoi beta-tester come se fossero la tua risorsa più importante, essi risponderanno diventando la tua risorsa più importante”
- "Quando hai perso interesse in un programma, l'ultimo tuo dovere è passarlo a un successore competente"

Confronto modelli: 
...


---

Core and Feeding of FOSS
Preso un dominio applicativo, analizziamo le "ere" del SW
1. Idea: qualcuno ha un'idea e la fa funzionare
2. Espansione e innovazione: il mondo se ne accorge e la tecnologia inizia a espandersi
3. Consolidamento: solo alcuni progetti hanno successo mentre altri sono assorbiti o falliscono.
4. Maturità: il mercato si riduce in un insieme di prodotti. L'innovazione rallenta in una pace moderata. E' difficile o impossibile per i nuovi competitor entrare nel mercato
5. FOSS Domination 
6. FOSS era (utopico): omologazione 

The emerging Economic Paradigm Of Open Source
Il SW per una azienda non è sempre un prodotto ma una tecnologia abilitante essenziale
E' importante distinguere i casi di tecnologia differenziante o non differenziante
E' differenziante se il cliente si accorge dei cambiamenti del SW e se il competitor non hanno accesso allo stesso SW, cioè abbiamo un vantaggio competitivo 

Confronto
Efficienza: quanti soldi per creare il prodotto do agli sviluppatori

...

Validare le impressioni
...

Vecchie sfide che si amplificano 
- Integrazione del SW
	- Modello a cascata: è una fase a sè stante
	- Modello microsoft: stabilize and syncronize, tutti lavoravano da soli e a fine giornata si metteva insieme il lavoro
	- Modello XP: piu volte al giorno, escludendosi a vicenda 
	- F/LOSS: continuamente e senza coordinamento a priori

Nuove sfide:
- Per evitare che il team si sfaldi, dobbiamo pensare a come comunicare, tenersi uniti, coordinarsi, ottenere collaboratori...
- Nascono nuovi strumenti di supporto per:
	- Comunicazione
		- Internet
		- Forum per mantenere la community unita e rispondere ai dubbi delle new entry
	- Sincronizzazione del lavoro e versioning
		- Sul codice: derivano molte conseguenze e eventuali problematiche
		- Sulla documentazione
	- Automatizzazione delle build: in un ambiente distribuito quando si fanno dei commit spesso github prova a compilare ed eseguire gli eventuali test.
	- Bug tracking con un certo rigore per indicare versione, log

SCM Source Code Management 
Scenari possibili:
- Sviluppatore che sta facendo un prodotto open-source da solo. Vuole distribuire il codice binario, e gli viene segnalato un bug di sicurezza in una versione precedente. E' necessario essere in grado di ritrovare qualsiasi versione precedente in qualsiasi momento dello sviluppo. 
- Necessità di condivisione di lavori con altri e gestirne l'accesso contemporaneo che potrebbe causare dei conflitti
- Necessità della tracciabilità dell'autore del codice

SW Configuration Management
Sono pratiche che hanno l'obiettivo di rendere sistematico il processo di sviluppo tenendo traccia dei cambiamenti in modo tale che il prodotto sia in ogni istante in uno stato ben definito

Gli oggetti di cui si controlla l'evoluzione sono detti configuration item o artifact
Inizialmente si versionavano file 
A volte fornisce supporto per la generazione del prodotto a partire da una determinata configurazione 
Non si salvavano tutto il file ma solo il diff rispetto al precedente

Le configurazioni sono l'insieme delle versioni dei vari file che convergono in una configurazione in un dato momento

Problemi:
- Gli aggiornamenti se falliscono solo nell'update di alcuni file, ho un inconsistenza: non c'è infatti un concetto di transazione
- Il renaming del file causa la perdita della storia del file 

Il versioning viene oggi fatto su directory e sotto-directory

Gli SCM sono per lo piu indipendenti da linguaggi di programmazione e applicazioni lavorando su file, preferibilmente su righe di testo
Evoluzione
- anni 80: strumenti locali
- anni 90: strumenti client-server centralizzati
- anni 2000: strumenti distribuiti peer-to-peer

Qualunque sistema si usi, occorre prendere decisioni importanti che influenzano la replicabilità della produzione
- Si traccia l'evoluzione anche di componenti esterni dal nostro controllo? (es librerie, compilatori)
- Si archiviano i file che costituiscono e costruiscono il prodotto?
Solitamente NO in quanto troppo costo e poco pratico, perdendo la perfetta replicabilità

Meccanismo base: ogni cambiamento è regolato da
- check-out: dichiara la volontà di lavorare partendo da una particolare revisione di un artifact
- check-in: dichiara la volontà di registrarne una nuova (change-set)
Queste operazioni vengono attivate rispetto a un repository, producendo spostamenti tra il repository e il mio workspace

Il repository mantiene informazioni quali date, tag, versioni, diramazioni/branches, autore...
La repository puo salvare solo le differenze tra una versione e l'altra
Puo essere centralizzata o distribuita (su qualunque pc c è sia la repo che il workspace. NON vuol dire che tutti hanno la stesso repo)

Regolamento del lavoro concorrente
Quando il repository è condiviso da un gruppo di lavoro, nasce il problema di gestirne l'accessi concorrente
- Modello pessimistico RCS: accesso agli artifact con mutua esclusione attivando un lock al check-out
- Modello ottimistico CVS: il sistema si disinteressa del problema e fornisce supporto per le attività di merge di change-set paralleli potenzialmente conflittuali
	E' possibile regolarlo parzialmente tramite rami paralleli di sviluppo, branch

SCM distribuito
Ogni peer ha una repository e non c'è sincronizzazione automatica 

Vantaggi
- lavoro offline
- velocità
- supporta diversi modi di lavorare 
	- simil centralizzato con una repository di riferimento
	- due peer che collaborano direttamente
	- gerarchico a più livelli

---

SE voglio ripensare il commit, git commit --amend 

git fetch per prendere dal repo remoto il diff rispetto al locale
- o faccio git merge
- o faccio git rebase 

git salva qualsiasi cosa aggiunge dei metadati, l hash con il tipo, lunghezza e contenuto del file
git checkout nomeBranch: sposta la HEAD, copia contenuto in index e nella Working directory pero magari parzialmente

git merge other: unisce cio che è puntato da head, cio che è puntato da other e il primo antenato comune

