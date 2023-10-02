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

Si è iniziato a capire che produrre codice non è solo scrivere codice ma bisogna anche risolvere dei problemi di comunicazione e bisogna essere rigorosi (Ipotesi di Bauer Zemanek: metodi formali riducono significamente gli errori di design o li eliminano anticipatamente; per essere realistici non sempre possiamo lavorare con metodi formali).
ci sono poi tanti aspetti da considerare in diversi momenti dello sviluppo

modellare ciclo di vita del SW
- identificare i vari passi e le attivita chiedendosu
	- cosa bisogna fare e fino a quando
	- chi lo debba fare

Studio di fattibilità 
Definizione preliminare del problema considerando il possibile mercato e i concorrenti
Studio di diversi scenari di realizzazione sia architatturale, HW, di personale interno o subappaltandolo
Stima dei costi, dei tempi di sviluppo, delle risorse necessarie e dei benifici delle varie soluzioni
Spesso questa fase di analisi si effettua in modo esterno per non sprecare risorse, per avere una visione esperta dando dei limiti temporali e di costi

Possibili output: un documento spesso in linguaggio naturale

Analisi e specifica dei requisiti
- comprendere il dominio applicativo
- identificare gli stakeholders 
- capire le funzioni richieste: capire cosa deve fare il sistema mentre il come è una fase piu avanti, quella di progettazione. 
	- Metodi esaustivi: in un linguaggio naturale 
	- metodi operazionali: modello eseguibile in qualche forma che fa vedere le caratteristiche che il modello deve rispettare
- Dal punto di vista dell utente, non gli interessa il progetto o l implementazione, ma quello che deve fare
	- Correttezza
	- Verificabilità: da linguaggio formale 

Output:
- Documenti di specifica
	- Documento contrattuale approvato dal committente
	- base per il lavoro del deisgner e di verifica
	- Importante quindi avere un documento formale
- Manuale utente o maschere di interazione 
- Piano dei testi di sistema, dei collaudi che certificano la correttezza
David Law: il valore dei modelli dipendono dalla vista presa ma nessuna è migliore per tutti gli scopi


Progettazione
Definizione dell'architettura del sistema
- scelta di una architettura SW di riferimento
- Scomposizione in moduli o oggetti
- Identificazioni di patterns

Programmazione e test di unità
- Le black box definite al punto precedente vengono realizzate
- lo sviluppatore deve avere testato i suoi moduli indipendentemente 
	- Utilizzo framework per il test (che ovviamente non consegnero all utente)
		- moduli stub/fittizzi (fittizzio cioe che in apparenza fa quello che dovrebbe fare in modo sicuro e semplice): moduli che la mia classe utilizza
		- moduli driver: moduli che usano la mia classe 

Output:
- insieme di moduli sviluppati separatamente con un interfaccia concordata e singolarmente verificati
- Unendo i vari componenti sono necessari
	- Test di integrazione: sottoinsieme dell'applicazione, sostituendo a mano i moduli di testing con i moduli reali
		- top-down
		- bottom-up

Manutenzione
- COrrettiva 
- Adattiva 
- Perfettiva

Output: ...

Altre attivita:
- documentazione : puo essere vista come attività trasversale o posteriore
- Verifica e controllo qualità
- gestione incentivi, responsabilità, eccezioni
- gestione delle configurazioni 


Modelli di ciclo di vita del SW
- Modello a cascata/document driven: ogni fase produce un semilavorato che è utilizzato dalla fase successiva senza possibilità di retroazione
nasce durante la fine degli anni 50 in un progetto militare
Famiglia di processi in cui in modo sequenziale 
...

Vantaggi:
Garantisce una buona separazione dei compiti

è possibile pianificare i tempi e monitoring dello stato di avanzamento ma è a senso unico

Svantaggi:
la manutenzione avviene post rilascio perche non è prevista retroazione (non si possono fare modifiche a specifiche, codice, documentazione...), è considerata una eccezione. ma il 70% dei costi di sviluppo ricadono in questa fase 
- Rigidita 
- Congelamento sotto prodotti, essendo vincolati a stime fatte nelle prime fasi
- monoliticita in quanto la pianificazione è orientata ad un singolo rilascio e la manutenzione è fatta solo sul codice 

- Modello a V: è come il modello a cascata che espande la fase di testing e chiarisce alcune relazioni. 
Dopo ogni fase si considera la coerenza con le specifiche del progetto 

Modelli
- prescrittivi: da un modo per procedere, quella giusta (spesso in realta incompleti)
- descrittivi: rappresentano una situazione prendendone solo alcuni aspetti perche non direttamente utilizzabili 


- Modello a cascata con singola retroazione alla fase precedente (iterazione ripetibile)
- Modello ciclo di vita a fontana: non vado alla fase precedente ma sempre al punto di partenza senza buttare quanto fatto anche se non so ogni volta quanto profonda di ogni zampillo sara. E' quindi un modello incrementale 

Modelli
- incrementale: quando nelle iterazioni viene inclusa la consegna. Quello che viene fatto dopo la consegna fa parte del processo
- iterativi: 

es implementazione iterativa:
- Stressa la modularizzazione e l'identificazione di sottosistemi e si ripetono fasi di coding ed integrazione
sviluppo incrementale
- viene esteso a tutte le fasi specifiche comprese
- la fase di manutenzione in senso stretto sparisce diventando semplice riciclo


- Modelli prototipali
Prototipo usa e getta, prima di buttarlo lo faccio vedere all'utente
prototipi:
- pubblici/esterni: lo presento al cliente per verificare di aver capito i requisiti per far compiere scelte all'utente
- privati/interni: per esplorare nuovi strumenti, linguaggi, diverse scelte per problemi difficili
Boehm Law protopizzazione diminuisce significativamente gli errori di progettazione e raccolta dei requisiti soprattutto per l'interfacce utente

è un modello iterativo perche il prototipo non glielo lascio davvero (non è incrementale perche non parto da quello)


Problemi con i modelli incrementali
- il lavoro di planning viene complicato in quanto lo stato del processo è meno visibile e bisogna pianificare tutte le iterazioni
- si riconosce che bisogna rimettere mano a cio che si è fatto MA il sistema potrebbe non convergere, non arrivando mai a qualcosa che consegno e non lo tocco piu
- cosa è un iterazione e quanto dura?
	- rischio di voler mettere troppo nella prima iterazione
	- rischio di overhead dovuto a troppe iterazioni
	- rischio di avere un eccessivo overlapping tra le iterazioni in quanto non si hanno feedback dell'utente

- Modello Pinball Life-Cycle (Ambler)
Il controllo che ho su cosa succede dopo è limitato
è una visione pessimistica di un processo indefinito in cui qualunque passo è possibile e quindi non è misurabile neanche in termini di vincoli temporali

- Modelli trasformazionali
Vediamo lo sviluppo del SW come un riffinamento di rappresentazioni formali del problema
Ad ogni passo vengono specializzate, ottimizzate e rese piu concrete attraverso trasformazioni automatiche o controllate. Deve essere dimostrabile che mantengo le stesse qualita precedenti

A partire da specifiche formali si ottiene un prototipo infatti
- differisce dal prodotto finale per efficienza e completezza
- passi di trasformazioni formalmente dimostrabili come corretti, portano ad avere la versione finale

- Modello a spirale
metamodello in quanto si usa per descrive altri modelli
è guidato dall'analisi dei rischi
Fasi
- Determinazioni obiettivi, alternative e vincoli
- Valutazione alternative, identificazione rischi
- Sviluppo e verifica
- Pianificazione fase successiva

ad ogni passo mi chiedo se ne valga la pena di continuare


- Modello spirale win-win
Evidenzia le comunicazioni con i clienti e che non sono di tipo pacifico ma necessitano di contrattazioni e negoziazione
Esplicita quindi il rischio di comunicazione


- Modello COTS Component Off The Shelf
prende a principio la riusabilità dei componenti sul mercato di moduli preesistenti, partendo da quelli mediante integrazione

Apre a nuovi problemi quali la classificazione dei moduli e il retrieval dei moduli
Servono degli adattatori per far convinvere componenti nati con assunzioni diverse (parametri diversi)
Rischio di importare codice inutile


Metodologie agili: eXtreme Programming
Valorizzare gli individui, responsabilizzare gli individui e il team non calando decisioni e deadline dall alto 
Valorizzare un SW che funziona piuttosto che una documentazione esaustiva
Collaborazione del cliente come se fosse nel team
Capacita di rispondere ai cambiamenti piuttosto che seguire il piano predisposto

