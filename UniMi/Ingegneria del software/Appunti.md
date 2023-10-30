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


GitFlow 
GitFlow è una tecnica di organizzazione dei branch e delle repository che prevede la creazione sia di diversi tipi di branch a vita limitata che il loro _merge_ guidato.

I branch e i tipi di branch previsti da GitFlow sono:
- branch master;
- branch develop;
- feature branches;
- release branches;
- hotfix branches.

In GitFlow, ci sono due branch che hanno una durata più lunga rispetto ai branch temporanei utilizzati per lavorare su specifiche funzionalità o correzioni di bug:
- **`master`**: contiene le versioni stabili del codice sorgente, pronte per essere consegnate o rilasciate al cliente o al pubblico. Queste versioni sono considerate _affidabili_ e _testate_, quindi possono essere utilizzate in produzione;
- **`develop`**: è il ramo di integrazione in cui vengono integrati i contribuiti di tutti i gruppi; è anche il punto di partenza degli altri tipi di branch.

Al termine di ogni rilascio, il contenuto del branch `develop` viene integrato nel branch `master`, che rappresenta la versione stabile del codice. Le _versioni notturne_, invece, sono versioni di sviluppo che vengono rilasciate periodicamente e contengono le ultime modifiche apportate al codice. Esse vengono create partendo dal branch `develop`, che rappresenta il punto di integrazione di tutti i contributi dei gruppi di lavoro.

I **_feature branch_** sono branch temporanei utilizzati per sviluppare nuove funzionalità o per correggere bug. **Possono essere creati solo a partire dal branch `develop`** e vengono utilizzati per isolare il lavoro su una specifica funzionalità o problema dal resto del codice. Quando il lavoro è completato, il feature branch viene integrato di nuovo nel `develop` tramite un merge. 

In questo modo, è possibile lavorare in modo organizzato su diverse funzionalità o problemi senza interferire tra loro. Per integrare il lavoro svolto in un feature branch nel branch `develop`, è necessario eseguire un merge del feature branch nel `develop`. Ci sono diversi modi di fare ciò, a seconda delle preferenze e delle esigenze specifiche. Un modo semplice di fare il merge è utilizzare il comando `git merge` dalla riga di comando. 
Se il merge non è possibile a causa di conflitti, sarà necessario risolverli manualmente prima di poter completare l’operazione. Una volta risolti i conflitti, sarà necessario creare un nuovo commit per finalizzare il merge.


Per iniziare una feature…

```
$ git checkout develop                  # entra nel branch develop 
$ git branch feature/myFeature          # crea un branch di feature 
$ git checkout feature/myFeature        # entra nel branch appena creato
```

Al termine della feature, integro:

```
$ git checkout develop                  # entra nel branch develop 
$ git merge --no-ff feature/myFeature   # mergia il branch di feature 
$ git branch -d feature/myFeature       # elimina il branch di feature
```


Di default, git risolve il merge di due branch con la stessa storia banalmente eseguendo il _fast forward_, ovvero spostando il puntatore del branch di destinazione all’ultimo commit del branch entrante.

In GitFlow è preferibile esplicitamente **disabilitare il fast forward** (con l’opzione `--no-ff`) durante il merge in `develop` in quanto è più facile distinguere il punto di inizio e il punto di fine di una feature.

Usando git è anche possibile eseguire in fase di merge lo _squashing_ dei commit, ovvero la fusione di tutti i commit del branch entrante in uno solo. Questa operazione è utile per migliorare la leggibilità della history dei commit su branch grossi (come `develop` o `master`) ma il suo uso in GitFlow è opinabile: il prof. Bellettini consiglia di non utilizzarlo, in modo da mantenere i commit originali.


Lo scopo di creare una release è **cristalizzare l’insieme delle funzionalità** presente sul branch `develop` all’inizio di essa dedicandosi solo alla sistemazione degli errori o alle attività necessarie per il deploy (modifica del numero di versione, …). L’insieme delle funzionalità rilasciate è quello presente sul branch `develop` al momento di inizio di una release.

I bug fix possono essere ri-mergiati in `develop`, anche utilizzando la funzionalità **cherry-pick** di git; essa permette di selezionare un commit specifico da un ramo e applicarlo in un altro ramo. 

Ad esempio, se si ha un ramo di sviluppo (“`develop`”) e un ramo di release (“`release`”), è possibile utilizzare il cherry-pick per selezionare solo i commit che contengono bugfix e applicarli al ramo di release, senza dover fare un merge di tutto il ramo di sviluppo. 

Ciò può essere utile in casi in cui si vuole mantenere la stabilità del ramo di release, includendo solo i bugfix considerati essenziali per la release.

Per iniziare una nuova release è sufficiente creare un nuovo branch da `develop`:

`$ git checkout -b release/v1.2.3 develop`

Al termine della creazione della release, è necessario fare il merge della release nel branch `master` e nel branch `develop`. Il merge in `master` rappresenta il rilascio della nuova versione del codice, che diventa disponibile per il pubblico o per il cliente. Il merge in `develop`, invece, integra le modifiche apportate durante la creazione della release nel branch di sviluppo, in modo che siano disponibili per le release future. 
In questo modo, è possibile gestire in modo organizzato il ciclo di vita del codice e il flusso di lavoro.

```
$ git checkout master               # entra nel branch master 
$ git merge --no-ff release/v1.2.3  # mergia la feature 
$ git tag -a v1.2.3                 # tagga sul branch master il rilascio 
$ git checkout develop              # entra nel branch develop 
$ git merge --no-ff release/v1.2.3  # mergia la feature 
$ git branch -d release/v1.2.3      # elimina il branch della feature
```

In git, i tag sono etichette che possono essere applicate a un commit per segnalarne l’importanza o per marcare un punto specifico dello storico del repository. 
Un **tag è un puntatore costante al commit** a cui è stato applicato, quindi non cambia mai e permette di fare riferimento in modo stabile a una versione specifica del codice. Al contrario, i branch sono puntatori dinamici che vanno avanti nel tempo, seguendo l’evoluzione del codice attraverso i nuovi commit

In GitFlow, le release sono versioni stabili del codice che vengono rilasciate al pubblico o al cliente. Ogni release viene creata partendo dal branch `develop` e viene gestita come un branch a sé stante, che viene chiuso una volta che tutte le modifiche previste sono state integrate. 

Al contrario, le feature sono branch temporanei utilizzati per sviluppare nuove funzionalità o per correggere bug. È possibile avere più feature aperte contemporaneamente, ma solo una release rimanere aperta in un dato istante.

Hotfix
Un _hotfix_ è una riparazione veloce di difetti urgenti senza dover aspettare la prossima release. È l’unico caso per cui non si parte da `develop`, ma dall’ultima - o una particolare - versione rilasciata su `master`.

`$ git checkout -b hotfix/CVE-123 master # crea un branch di hotfix`

Quando lo chiudo:

```
$ git checkout master                   # entra nel branch master 
$ git merge --no-ff hotfix/CVE-123      # mergia l'hotfix 
$ git tag -a hotfix/CVE-123             # tagga sul branch master il rilascio 
$ git checkout develop                  # entra nel branch develop 
$ git merge --no-ff hotfix/CVE-123      # mergia l'hotfix 
$ git branch -d hotfix/CVE-123          # elimina il branch di hotfix
```



Limiti
git e GitFlow come sono stati esposti presentano numerosi vincoli, tra cui:
- la **mancanza di un sistema di autorizzazione granulare**, ovvero la possibilità di assegnare permessi in modo specifico e mirato a diverse funzionalità o risorse. Inoltre, non esiste una distinzione tra diversi livelli di accesso, quindi o si ha accesso completo a tutte le funzionalità o non si ha accesso a niente;
- l’**assenza di code review**, ovvero il processo di revisione del codice sorgente da parte di altri sviluppatori prima che venga integrato nel codice base.

Il tool `git request-pull` è un comando di git che serve per formattare e inviare una proposta di modifiche a un repository tramite una mailing list. Il comando crea un messaggio di posta elettronica che chiede al maintainer del repository di “pullare” le modifiche, ovvero di integrarle nel codice base. 
Oggi, questa pratica è stata in molti progetti sostituita dalle pull request, che sono richieste di integrazione delle modifiche presentate attraverso un’interfaccia web. Le pull request offrono una serie di vantaggi rispetto alle richieste via email, come una maggiore trasparenza del processo di integrazione, una maggiore efficienza e una maggiore facilità di utilizzo.

La sintassi del comando è la seguente:
`git request-pull [-p] <start> <URL> [<end>]`

Per esempio, i contributori Linux usano questo strumento per chiedere a Linus Torvalds di unire le modifiche nella sua versione. L’output generato mostra file per file le modifiche fatte e i commenti dei commit creati, raggruppati per autore.

Questo modello è molto più _peer to peer_ delle pull request proposte dai sistemi semi-centralizzati spiegati in seguito.


---

Un hosting centralizzato Git è un servizio che fornisce una repository centrale per i progetti Git dove i contributi vengono integrati e gestiti, garantendo una maggiore trasparenza e controllo del processo di sviluppo e mantenendo molti vantaggi della decentralizzazione, come la possibilità di lavorare in modo asincrono e autonomo.

Gli hosting centralizzati come GitHub e GitLab nuovi meccanismi e provano a imporre nuovi workflow, come il GitHub Flow o il GitLab Flow, per semplificare e ottimizzare il processo di sviluppo. 
Inoltre, molti servizi di hosting centralizzati offrono funzionalità aggiuntive, come la possibilità di eseguire il fork di un repository, inviare pull request per le modifiche e di utilizzare strumenti di Continuous Integration CI per testare automaticamente le modifiche apportate al codice.


Fork
Il “fork” di un repository Git è una **copia del repository originale** che viene creata su un account di hosting diverso dal proprietario originale. 
Questo permette a un altro sviluppatore di creare una copia del repository e di lavorare su di essa senza influire sul lavoro del proprietario originale e **senza la sua autorizzazione**. È possibile quindi mantenere una _connessione_ tra i due repository e condividere facilmente le modifiche apportate.

La maggioranza delle piattaforme di hosting centralizzato **ottimizza la condivisione dello spazio degli oggetti**, utilizzando un’unica _repository fisica_ per tutti i fork. 

Tuttavia, questo può comportare alcune problematiche di sicurezza, come ad esempio la difficoltà per la piattaforma di stabilire in quale fork si trova un determinato oggetto in caso di conflitto o la possibilità che un utente malintenzionato possa modificare o eliminare accidentalmente oggetti di altri fork. 
Per questo motivo, è importante che le piattaforme implementino **misure di sicurezza adeguate** per proteggere i dati dei fork e garantire la tracciabilità delle modifiche


Pull request 
Tra la creazione di una pull request e il suo _merge_, specialmente nei progetti open source (dove chiunque può proporre qualsiasi patch) è fondamentale prevedere un processo di **review**.

La funzionalità di _review/pull request_ permette di facilitare le interazioni tra gli sviluppatori utilizzando il sito di hosting come luogo comune per la discussione informale e la revisione delle modifiche.
Problemi: SE il develop avanza, le mie modifiche diventano incompatibili

CI
Molti servizi di hosting centralizzati offrono strumenti di **continuous integration** (CI) che possono essere utilizzati per testare automaticamente le modifiche proposte nella pull request. 
Questi strumenti consentono di verificare che le modifiche non introducano errori o vulnerabilità e di garantire che il codice sia pronto per essere integrato nel repository principale. 
Possono essere utilizzati anche per eseguire automaticamente la _suite di test_ o automatizzare il deployment.


Gerrit
Gerrit è un **sistema di review** del codice sviluppato internamente da Google per gestire i progetti interni; si basa sul concetto di “peer review”: tutti gli sviluppatori sono autorizzati a fare review delle proposte di modifica di qualsiasi zona di codice.

Pensa git come due repository, uno in cui possono fare fetch e un altro in cui si possa fare push e su cui verranno fatte le review.

Nel processo di review di Gerrit, i **developer** possono sottoporre proposte di cambiamento utilizzando un sistema di “patch” che descrive le modifiche apportate al codice. 
I **reviewer**, ovvero gli altri sviluppatori del progetto, possono quindi esaminare le patch e decidere se accettarle o rifiutarle. Una volta che una patch ha ricevuto un numero sufficiente di review positivi, viene automaticamente integrata nel **repository principale autoritativo** in cui tutti hanno accesso in sola lettura.

Gerrit obbliga a strutturare le modifiche (_changeset_) in un unico commit (tecnica _squash_) al momento dell’accettazione. 
Ciò significa che tutte le modifiche apportate devono essere fuse in un unico commit, in modo da rendere più facile la gestione del repository. 
Al momento della review, invece, le modifiche rimangono separate in versioni singole, ovvero ogni modifica viene presentata come un commit separato, in modo che i reviewer possano esaminarle più facilmente.

Il verifier è uno strumento o un processo che viene utilizzato in Gerrit per verificare che le modifiche proposte siano corrette e funzionino come dovrebbero. 
In particolare, il verifier scarica la patch, la compila, esegue i test e controlla che ci siano tutte le funzioni necessarie. 
Se il verifier rileva dei problemi, può segnalarli al team di sviluppo perché vengano corretti prima che la patch venga accettata.

Una volta verificata, una proposta di modifiche deve essere anche approvata. 
L’approvatore deve determinare la risposta alle seguenti domande riguardo la proposta di modifiche (questa figura ha una conoscenza piu generale del progetto e dei suoi scopi, decidendo se sia coerente):
- _è valida per lo scopo del progetto?_
- _è valida per l’architettura del progetto?_
- _introduce nuove falle nel design che potrebbero causare problemi in futuro?_
- _segue le best practices stabilite dal progetto?_
- _è un buon modo per implementare la propria funzione?_
- _introduce rischi per la sicurezza o la stabilità?_

Se l’approver ritiene che la proposta di modifiche sia valida, può approvarla scrivendo “LGTM” (acronimo di _“Looks Good To Me”_) nei commenti della pull request.


Build automation
La build automation è un processo fondamentale nello sviluppo di software open source, che consiste nel creare un sistema automatizzato per compilare il codice sorgente in un eseguibile. 

Questo processo è importante perché consente di risparmiare tempo e risorse, evitando di dover compilare manualmente il codice ogni volta che si apportano modifiche. Inoltre, la build automation garantisce una maggiore qualità e coerenza del software, poiché il processo di compilazione viene eseguito in modo uniforme ogni volta.

Make
`make` è uno strumento di build automation che viene utilizzato per automatizzare il processo di compilazione di un progetto. In particolare, `make` viene utilizzato per specificare come ottenere determinati _targets_ (obiettivi), ovvero file o azioni che devono essere eseguite, partendo dal codice sorgente. 

Ad esempio, in un progetto di sviluppo software, un _target_ potrebbe essere il file eseguibile del programma, che viene ottenuto compilando il codice sorgente. `make` segue la filosofia _pipeline_, ovvero prevede l’utilizzo di singoli comandi semplici concatenati per svolgere compiti più complessi.

È supportata la _compilazione incrementale_, ovvero il fatto di compilare solo le parti del progetto che sono state modificate dall’ultima volta, al fine di velocizzare il processo. 
Inoltre, vengono gestite le _dipendenze_ tra file, ovvero le relazioni tra i diversi file che compongono il progetto: se un file sorgente dipende da un altro file, make assicura che il file dipendente venga compilato solo dopo che il file da cui dipende è stato compilato. 

Ciò garantisce che il progetto venga compilato in modo coerente e che le modifiche apportate a un file siano considerate correttamente nella compilazione dei file dipendenti.

Svantaggi:
Tuttavia, make lavora a un livello molto basso, il che può rendere facile commettere errori durante la sua configurazione e utilizzo.
Non c’è portabilità tra macchine (ambienti) diverse.


Makefile
Un _Makefile_ è un file di testo che contiene le istruzioni per il programma make su come compilare e linkare i file sorgente di un progetto. Ogni riga del Makefile definisce un obiettivo o una dipendenza, insieme ai comandi che devono essere eseguiti per raggiungerlo. 

L’utilizzo del Makefile permette di automatizzare la compilazione e il linkaggio dei file sorgente, semplificando il processo di sviluppo di un progetto. 
Sono stati creati dei tool (`automake`, `autoconf`, `imake`, …) che _generano_ `Makefile` ad-hoc per l’ambiente attuale.

Il _mantra_:
```
$ ./configure 
$ make all 
$ sudo make install
```
era largamente utilizzato per generare un Makefile ad-hoc per l’ambiente attuale e installare il software sulla macchina in modo automatico. `automake`, `autoconf`, e `imake` sono strumenti che aiutano a questo scopo, generando Makefile che possono essere utilizzati per compilare e installare il software in modo automatico.


Ant
Ant nasce in Apache per supportare il progetto Tomcat. 
Data una **definizione in XML** della struttura del progetto e delle dipendenze invocava comandi programmati tramite classi Java per compilare il progetto.

Il vantaggio è che Java offre un livello d’astrazione sufficiente a rendere il sistema di build portabile su tutte le piattaforme.

Non solo compila, ma fa anche deployment. 
Il deployment consiste nell’installare e configurare un’applicazione o un sistema su uno o più server o ambienti di esecuzione. 
Nel contesto di Ant, il deployment può includere l’invocazione di comandi per copiare i file del progetto sui server di destinazione, configurare le impostazioni di sistema o dell’applicazione, avviare o fermare servizi o processi, e così via. In questo modo, Ant può essere utilizzato non solo per compilare il progetto, ma anche per distribuirlo e rendere disponibile l’applicazione o il sistema ai suoi utenti.

I target possono avere dipendenze da altri target. I target contengono task che fanno effettivamente il lavoro; si possono aggiungere nuovi tipi di task definendo nuove classi Java.


Gradle 
Gradle è uno strumento di build automation che utilizza le repository Maven come punto di accesso alle librerie di terze parti. 
Maven è una piattaforma di gestione delle dipendenze e della build automation per il linguaggio di programmazione Java. Le repository Maven sono archivi online che contengono librerie Java, plugin e altri componenti utilizzati nella build di progetti Java.
Gradle utilizza queste repository per cercare e scaricare le librerie di cui ha bisogno per eseguire la build del progetto.

Gradle, che supporta Groovy o Kotlin come linguaggi di scripting, adotta un approccio dichiarativo e fortemente basato su convenzioni. 
Ciò significa che tutto ciò che è già stato definito come standard non deve essere ridichiarato. 
Inoltre, Gradle definisce un linguaggio specifico per la gestione delle dipendenze e permette di creare build multi-progetto.

Gradle scala bene in complessità: permette di fare cose semplici senza usare le funzioni complesse. È estendibile tramite plugin che servono per trattare tool, situazioni, linguaggi definendo task e regole per lavorare più facilmente.

Il plugin _Java_ definisce:
- una serie di **sourceSet**, ovvero dove è presente il codice e le risorse. Principalmente sono:
    - `src/main/java`: sorgenti Java di produzione;
    - `src/main/resources`: risorse di produzione;
    - `src/test/java`: sorgenti Java di test;
    - `src/test/resources`: risorse di test.
- dei **task**, anche con dipendenze tra loro.

Bug Tracking
Il bug tracking è stato reso necessario nel mondo open source per via della numerosità dei contributi e della alta probabilità di avere segnalazioni duplicate.

Inoltre, per gestire le segnalazioni di bug nell’ambito dello sviluppo open source, esistono diversi strumenti come git-bug, BugZilla, Scarab, GNATS, BugManager e Mantis.

L’obiettivo del bug tracking è avere più informazioni possibili su ogni bug per saperli riprodurre e quindi arrivare a una soluzione.

È importante verificare i bug una volta che l’_issue_ è stato aperto, in modo da poter confermare la sua esistenza e la completezza delle informazioni fornite.

Un _issue_ è un problema o una richiesta di funzionalità segnalata all’interno di un progetto di software. 
Gli issue vengono solitamente utilizzati per tenere traccia dei problemi noti o delle richieste di nuove funzionalità all’interno di un progetto, e possono essere gestiti attraverso un sistema di bug tracking o gestione delle richieste. 
Gli issue possono essere aperti da qualsiasi membro del team o dalla comunità, e possono essere risolti o chiusi da un membro del team responsabile.

Ci sono diversi modi per cui può essere chiuso un bug:
- **duplicate**: quando è stato già segnalato in precedenza e quindi non rappresenta un problema nuovo. In questo caso, viene solitamente fatto riferimento al numero del bug originale che ha già ricevuto una risoluzione;
- **wontfix**: il bug viene chiuso come “non risolvibile” perché o rappresenta una funzionalità voluta dal progetto o è troppo complesso da risolvere per essere considerato conveniente farlo dal punto di vista dei progettisti;
- **can’t reproduce**: non è stato possibile riprodurre il bug, ovvero che non è stato possibile ottenere lo stesso risultato o il comportamento segnalato dal bug. Ciò può essere dovuto a una mancanza di dettagli o a un errore nella segnalazione del bug stesso;
- **fixed**: il bug è stato fixato; vs **fix verified**: il fix è stato integrato in una release passando tutti gli step di verifica.
Il  bug tracking è sempre piu integrato con il versioning



Unified Process
è una metodologia di organizzazione che utilizza UML
è un processo che si definisce allo stesso 
- sequenziale: in quanto esistono 4 fasi svolte in sequenza
- iterativo: ogni fase è svolta in maniera iterativa 
- incrementale in cui ogni cilo delle 4 fasi porta a una release 


Progettazione
Refactoring: 
Cambiare il design del codice senza cambiarne il funzionamento
Durante il refactoring è opportuno rispettare le seguenti regole:
- le **modifiche al codice non devono modificare le funzionalità**: il refactoring DEVE essere invisibile al cliente;
- **non possono essere aggiunti test aggiuntivi** rispetto alla fase verde appena raggiunta.

Se la fase di refactoring sta richiedendo troppo tempo allora è possibile fare rollback all’ultima versione verde e **pianificare meglio** l’attività di refactoring. 
Vale la regola del _“do it twice”_: il secondo approccio a un problema è solitamente più veloce e migliore.

Spesso le motivazioni dietro un refactoring sono:
- precedente **design molto complesso e poco leggibile**, a causa della velocità del passare ad uno _scenario verde_;
- **preparare il design di una funzionalità** che non si integra bene in quello esistente; dopo aver raggiunto uno _scenario verde_ in una feature, è possibile che la feature successiva sia difficile da integrare. In questo caso, se il _refactoring_ non è banale è bene fermarsi, tornare indietro e evolvere il codice per facilitare l’iterazione successiva (**design for change**).
- presenza di **debito tecnico** su lavoro fatto in precedenza, ovvero debolezze e “scorciatoie” che ostacolano notevolmente evoluzioni future.

Design knowledge
La design knowledge è la **conoscenza del design** architetturale di un progetto
Questa conoscenza nasce da 
- nostra memoria: non è efficace perché nel tempo si erode
- documenti di design: se non viene aggiornato di pari passo con il codice rimane disallineato, risultando più dannoso che d’aiuto
- piattaforme di discussione / issue management / version control: le informazioni sono sparse in luoghi diversi e di conseguenza difficili da reperire e rimane il problema di mantenere aggiornate queste informazioni. 
- Modelli specializzati (UML) (model driven design): diagrammi UML si è cercato di sfruttare l’approccio _**generative programming**_, ovvero la generazione automatica del codice a partire da specificazioni di diagrammi. Con l’esperienza si è visto che non funziona.
- codice: è possibile capire il design ma è difficile rappresentare le ragioni della scelta


Per condividere tali scelte di design (il _know how_) è possibile sfruttare:
- **metodi**: con pratiche (come Agile) o addirittura l’object orientation stessa, che può essere un metodo astratto per condividere scelte di design.
- **design pattern**: fondamentali per condividere scelte di design, sono utili anche per generare un vocabolario comune (sfruttiamo dei nomi riconosciuti da tutti per descrivere i ruoli dei componenti) e aiutano l’implementazione (i pattern hanno delle metodologie note per essere implementati). I pattern non si concentrano sulle prestazioni di un particolare sistema ma sulla generalità e la riusabilità di soluzioni a problemi comuni;
- **principi**: per esempio i principi SOLID.


OO Object Orientation 
- Ereditarietà: definire una classe ereditando proprietà e comportamenti di un’altra classe.
- Polimorfismo: quando una classe può assumere diverse forme in base alle interfacce che implementa. Il collegamento tra capacità e oggetto è fatto **a tempo di compilazione**: non è importante quindi se la capacità non è ancora definita;
- Composizione 
- Dynamic Pipeling: in Java il tipo concreto degli oggetti e quindi il problema di stabilire _quale metodo chiamare_ viene risolto durante l’esecuzione

Composizione >>>> Ereditarietà

Principi SOLID
- Single Responsability: una classe, un solo scopo. Così facendo, le classi rimangono semplici e si agevola la riusabilità.
- Open close Principle: classe aperte ai cambiamento ma chiuse ai cambiamenti delle parti già in produzione.
- Liskov Substitution Principle: si collega all’aspetto **contract-based** del metodo Agile: le _precondizioni_ di un metodo di una classe figlia devono essere ugualmente o meno restrittive del metodo della classe padre. Al contrario, le _postcondizioni_ di un metodo della classe figlia non possono garantire più di quello che garantiva il metodo nella classe padre. Fare _casting_ bypassa queste regole.
- Interface Segregation: più le capacità e competenze di una classe sono frammentate in tante interfacce più è facile utilizzarla in contesti differenti. Meglio quindi avere **tante interfacce specifiche** e piccole (composte da pochi metodi), piuttosto che poche, grandi e generali.
- Dependency Inversion: il codice dal quale una classe dipende non deve essere più **concreto** di tale classe. Le cose astratte non dovrebbero dipendere da classi concrete

---

Reference escaping: accesso a un attributo privato fuori dalla classe
Situazioni:
- Getter che ritorna un riferimento 
- Setter che assegna ad un attributo privato un riferimento che gli viene passato
- Costruttore che assegna ad un attributo segreto un riferimento che gli viene passato

Encapsulation e information hiding
Parnas L8: solo cio che è nascosto puo essere cambiato liberamente e senza pericoli 
Scopi:
- facilitare la comprensione del codice, definendo le responsabilità
- rendere piu facile modificarne una parte senza danni

Immutabilità
Classe in cui non c è modo di cambiare lo stato dell'oggetto dopo la sua inizializzazione
Condizione:
- NON fornire metodi che mutano lo stato
- (non è obbligatorio che gli attributi siano privati)
- ha TUTTI gli attributi final
- Assicura l'accesso esclusivo a tutte le parti non immutabili

Code smell:
- codice duplicato
- Metodo "troppo" lungi
- Troppi livelli logici di indentazione 
- Troppi attributi per classe
- Lunghe sequenze di if-else o switch
- classe troppo grande
- lista di parametri troppo lunga
- numeri magici
- commenti 
- nomi oscuri o inconsistenti
- codice morto
- getter e setter --> rinuncio a responsabilità

es mazzo di carte da 52 carte, 4 semi, 13 valori


type abstraction: diamo un nome ai concetti
nel nostro es, al mazzo e alle carte

un enum per ogni valore definisce un unico oggetto immutabile e condiviso
List con Generico è piu difficile da gestire di un array

...

Polimorfismo: l oggetto dice di poter accettare oggetti diverse forme
Interface segmentation: un oggetto si presenta con piu forme

Collegamento dinamico: permette di scrivere una chiamata che chiamera un codice che non esiste ancora

---

UML diagram
Freccia: relazione tra classi/oggetti
- freccia bianca tratteggiata da classe a interfaccia: la classe implementa l'interfaccia
- freccia nera tratteggiata da classe a classe / da classe a interfaccia: la classe ha una dipendenza rispetto all'altra
- freccia con rombo da classe a classe: legame tra istanze, (se bidirezionale non metto la freccia)
	- associazione, 
	- aggregazione (rombo bianco): legato a qualcosa di esterno che mi definisce
		Metodo implementativo: l'attributo
	- composizione (rombo nero): deve essere un contenimento fisico. Requisiti
		- L'oggetto contenuto deve essere presente nella SOLA classe contenente 
		- La vita dell oggetto contenuto sia legata al contenente 
		Metodo implementativo: classe statica inner
	minimo..massimo di istanze

corsivo: oggetto non concreto (ATT classe che implementa un metodo in corsivo, sarà presente nell UML in quanto ha tale metodo come concreto)
Per essere concreto: NON devo avere metodi astratti
Per essere astratto: non c è un vincolo in quanto nonostante abbia tutti i metodi concreti potrei decidere di restare astratta

\<\<stereotipo>>
sottolineatura: quando un metodo/attributo è statico 

Attributo: 
- pubblico: verde
- protected: giallo
- private: rosso


Pattern: sono soluzioni a problemi ricorrenti
è uno strumento concettuale che cattura la soluzione per una famiglia di problemi e che esprime architetture vincenti

Antipattern: denuncia di una soluzione sbagliata anche se ragionevole ad un problema

Idioma: un modo di risolvere il pattern dipendente dal linguaggio

Meta pattern: pattern con cui pensiamo i pattern, identifica due elementi base
- HookMethod: metodo astratto che determina il comportamento specifico nelle sottoclassi
	- Punto caldo in cui si puo intervenire per personalizzare, adattare lo schema 
- TemplateMethod: metodo che coordina generalmente piu hook method
	- Punto freddo di invaribilità del pattern

Come si relazionano hook e template
- Unification: template e hook sono nella stessa classe del framework
- Connection: template e hook sono in classi separate tra di loro collegate da una associazione
- Recursive connection: template e hook sono in classi tra di loro collegate anche tramite relazione di generalizzazione

Gang of Four Patterns: definisce 23 patter e li classifica in tre categorie
- Creazionali: creazione degli oggetti
- Comportamentali: interazioni tra gli oggetti
- Strutturali: composizioni di classi e oggetti

- Singleton pattern: si vuole avere un oggetto e non una classe
Approccio lazy: ritardare la creazione dell oggetto
...
Brutta soluzione: NON è thread safe
Soluzione: usare syncronized nel metodo getInstance, che implica un controllo se qualcuno ha gia il lock sul metodo della classe
Problema: non è ottimale dal punto di vista delle prestazioni
Soluzione: usare syncronized SOLO dentro all if del null facendo poi nuovamente il controllo: double check

ATTTTTT In Java non facciamo cosi

Idioma Java con cui si fa Singleton:
...

usando un enumerabile, quando lo utilizzo la prima volta la creazione è thread safe grazie alla VM e otteniamo quello che volevamo: un unico oggetto accessibile, condiviso e immutabile

- Iterator pattern: fornisce un modo di accedere agli elementi di un oggetti in maniera sequenziale senza esporne la rappresentazione

oltre a Iterator ho Iterable che dipende da Iterator

Con il for each dico esplicitamente che non voglio fare il remove
se voglio farlo iterabile su due cose: i tipi generici si vedono a tempo di  compilazione e poi spariscono quindi NON posso 

Nullability
ad una variabile che indica un riferimento a un oggetto allora possiamo assegnarci un valore null
Problema: quando proviamo a deferenziare la variabile e non puntando a nulla, riceviamo un errore

...

come implementare attributi diversi da null: 
assert attributo!=null;

modalita sviluppo: faccio un if --> segnalo io l errore dell utilizzatore, programmazione difensiva
modalita produzione: assert o notazione --> assumo l utilizzo corretto, programmazione con contratto

---

@ParamerizedTest 
	@CsvSource {"1, 1 <- Top", "1 2, 1 2 <- Top"}
void test(String program, String output){
...
}

cercare plugin per regex
imparare le regex sulle stringhe

...

