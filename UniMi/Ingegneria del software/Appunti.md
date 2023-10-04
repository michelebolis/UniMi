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
- Valorizzare gli individui, responsabilizzare gli individui e il team non calando decisioni e deadline dall'alto 
- Valorizzare un SW che funziona piuttosto che una documentazione esaustiva
- Collaborazione del cliente come se fosse nel team
- Capacita di rispondere ai cambiamenti piuttosto che seguire il piano predisposto

