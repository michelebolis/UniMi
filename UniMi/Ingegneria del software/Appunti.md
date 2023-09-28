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