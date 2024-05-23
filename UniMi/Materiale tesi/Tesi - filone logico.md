Nei dataset sono spesso presenti informazioni personali e sensibili di vari individui, che come tali non devono essere rilasciate pubblicamente.
Il problema che si vuole risolvere è quindi quello di una eliminazione selettiva di tali informazioni nel nostro db, con l'obiettivo ultimo di renderlo pubblico.

Un primo modo per indicare cosa sia sensibili, è `specificando esplicitamente la label` del nodo o il nome della proprietà o il nome della relazione.
Un approccio invece piu evoluto è quello di specificare `categorie sensibili` come per esempio "stato medico", "geolocalizzazione", "situazione economica"

Una "raffinatura" dell'individuazione di ciò che è veramente sensibile, può essere l individuazione delle label che rappresentano delle persone. Le informazioni di altre figure come aziende e organizzazioni non sono da considerare come personali e quindi non "gestite" dal GDPR.


(C27) Il presente regolamento non si applica ai dati personali delle persone decedute
Fonte: https://www.garanteprivacy.it/garante/document?ID=6264597

...

Sono state poi definite delle funzioni per analizzare il db sia prima la sua sanitizzazione sia eventualmente dopo.
Innanzitutto quantifichiamo la `numerosità dei nodi e delle relazioni` presenti nel db.
Contiamo poi il numero di ciascuna label, che è state segnalata come pericolosa, ed eventuali nodi senza alcuna label. 
Passando invece alla relazioni elenchiamo `per ogni label il tipo di relazione` che collega il nodo associato alla label con altri nodi. Dividiamo le relazioni in entranti e uscenti cosicché si possano evidenziare alcuni pattern. 

es
In questo esempio i nodi con label "Phone", "Email" e "Officer" non hanno relazioni verso altri nodi ma hanno solo relazioni entranti 
![[Pasted image 20240325091535.png]]
![[Pasted image 20240325095320.png]]

Un altro esempio significativo è quando nonostante siano presenti 241 relazioni "KNOWS_SN" (considerando che ci sono 369 "Person"), in realtà 331 nodi non hanno questa relazione, quindi 241 relazioni sono uscenti dai 58 nodi restanti
![[Pasted image 20240325095403.png]]

Passando poi alle proprietà dei nodi, dato l'elenco delle parole pericolose (ottenuto in qualsivoglia modo), analizziamo data una label se contiene delle proprietà pericolose.
Considerando che un nodo non puo avere due proprietà con la stessa key, è possibile verificare quale siano le proprietà pericolose sempre presenti o meno.
Eseguiamo la stessa procedura con le proprietà non considerate pericolose. 
Analogamente consideriamo le proprietà presenti nelle relazioni ed eseguiamo quanto appena fatto con i nodi.
es
In questo esempio si evince che, nel caso in cui eliminassi tutte le proprietà email_address da Email, i nodi resterebbero senza proprietà, mentre invece Officer perderebbe solo la metà delle proprietà
![[Pasted image 20240325153937.png]]

Analizzando invece i nodi, possiamo individuare i nodi senza alcuna relazione (isolati) che, nonostante possano contenere delle informazioni sensibili, potrebbero essere ignorati
Motivo
(C26) I principi di protezione dei dati non dovrebbero pertanto applicarsi a informazioni anonime, vale a dire informazioni che non si riferiscono a una persona fisica identificata o identificabile o a dati personali resi sufficientemente anonimi da impedire o da non consentire più l'identificazione dell'interessato. Il presente regolamento non si applica pertanto al trattamento di tali informazioni anonime, anche per finalità statistiche o di ricerca.

Inoltre individuiamo anche il nodo centrale, definito come il nodo con il maggior numero di relazioni. Considerando infatti che l'eliminazioni di un nodo deve essere preceduta dall'eliminazioni di tutte le sue relazioni, se il nodo centrale contenesse delle informazioni sensibili, avremmo una perdita considerevole di informazioni

looser association: forse troppo quindi si fa cluster 
k-anonimity: approccio di anonimizzazione generalizzazione o soppressione (se ho poche 
Richiede che ciascun dato sia indistinguibile da almeno un certo numero di soggetti, k
Maggiore è k e maggiore sarà la protezione
Requisiti: microdata tables 
In base alle loro caratteristiche, gli attributi possono essere divisi in
- attributi identificativi
- attributi quasi identificativi
- attributi sensibili
- attributi non sensibili

De identificando (togliendo gli attributi identificativi) non garantisce l anonimato a causa degli attributi quasi identificativi
Togliendo sia attributi identificativi che quasi identificativi, avremmo l anonimato ma perderemmo una grande porzione 
Metodi per il k-anonymity:
- modificare i quasi identificatori rimpiazzandoli con un valore piu generico
- soppressione degli outliner

Come la k-anonymity puo essere rafforzato nella pratica
La generalizzazione puo essere applicata a livello del valore o a livello dell'attributo o a livello di record
Famiglie di approcci
- Gerarchie: gerarchie di generalizzazioni pre definite per ogni quasi identificativo
La nozione di dominio dell attributo viene esteso a dominio generalizzato, cioe dominio esteso ai valori generalizzati
es
![[Pasted image 20240410092709.png]]

Il problema di generare k-anonymous dataset minimizzando le generalizzazioni è provato essere un problema NP-hard
Approcci:
- Cercare nell albero binario nel dominio generalizzato invece che nel dominio
Si definisce una soglia MaxSup che rappresenta il numero massimo di soppressione accettabili in un record
A binary search is adopted to determine the lowest level at which there is an element that corresponds to a k-anonymous dataset respecting the MaxSup constraint
To avoid to compute the datasets to check for the k-anonymity requirement, the approach in [62] builds on the notion of (lattice of) distance vectors representing distances among the generalized domains, by means of which it is possible to check the satisfaction of k-anonymity without computing the actual corresponding datasets.

- Recording: generalizza il valore del quasi identificativo in intervalli a runtime
...

Alternative:
- Data fragmentation: alternativa alla generalizzazione che consiste in un taglio verticale

es
![[Pasted image 20240410095014.png]]
- Micro aggregazione

es
![[Pasted image 20240410095131.png]]


Fonte: https://spdp.di.unimi.it/papers/tdp2023.pdf, https://spdp.di.unimi.it/papers/tkde_k-anonymity.pdf

tuple outliner, è meglio eliminare (prendo in input quanto al massimo voglio perdere))
quando non posso cancellare?
- cifrare (AES https://pycryptodome.readthedocs.io/en/latest/src/examples.html#encrypt-data-with-aes)
- gerarchie di generalizzazioni 


ATT lo spezzare va bene quando è pericolosa l associazione tra due nodi 

- NER per sostituire le liste
	- https://www.nltk.org/api/nltk.classify.positivenaivebayes.html
- mismatching words 
	- https://github.com/seatgeek/thefuzz

(PRIMA BOZZA PASSATA)
\textbf{
Tutte le informazioni sono oggi come in passato conservati in una qualche modo o forma a seconda dell'utilizzo che si prospetta di fare con essi.
}
\textbf{
La quantità e la interconnettività dei dati sono tuttavia aumentati con l'era digitale, portando a nuove possibilità.
I database a grafo cercano di risolvere o facilitare uno dei trend commerciali degli ultimi decenni, ovvero l'analisi e la comprensione di dati non strutturati estremamente connessi.
}
\textbf{
Consideriamo lo scenario in cui, per fini di ricerca o commerciali, si voglia rendere disponibile la nostra base di dati attraverso delle API o pubblicandone il dump. 
}
\textbf{
\'E molto probabile che siano presenti informazioni personali e sensibili di vari individui che come tali non devono essere rilasciate pubblicamente in modo chiaro, in ottemperanza alla normative europee.
Il problema che si vuole risolvere è quindi quello di una sanitizzazione selettiva di tali informazioni nel nostro database.
Dobbiamo però considerare che i dati, non essendo strutturati, non seguono uno schema come avviene per esempio nei database relazionali.
}
\textbf{
Al proprietario/amministratore della base di dati è necessario richiedere di indicare ciò che, in base al contesto delle informazioni contenute nel database, è da considerare sensibile. 
Questa indicazione potrebbe essere fatta in modo diretto, richiedendo l'elenco delle chiavi delle proprietà che si considerano pericolose, e quindi che andrebbero sanitizzate.
In questo lavoro tuttavia richiederemo la specifica più ad alto livello delle informazioni sensibili, richiedendo quali dei contesti disponibili sia da considerare pericoloso.
}
Identificazione dei dati sensibili
Per l'individuazione delle proprietà pericolose da pubblicare, all'utilizzatore del tool viene richiesto un sottoinsieme dei contesti disponibili. 
Neo4j ci permette di ricavare tutte le chiavi distinte delle proprietà presenti sia nelle relazioni che nei nodi. Dividiamo questi due casi in quanto le query ad essi associato saranno diverse.
Inizialmente consideriamo tali chiavi come rappresentative del valore ad esse associate, tuttavia come poi riscontreremo, ad una chiave generica potrebbero in realtà essere associati informazioni sensibili.
La prima fase consiste nell'estrazione, dato un contesto, delle keyword ad esso associato, che abbiamo definito in una lista.
Una prima soluzione sarebbe quella di considerare pericolosa una chiave di una proprietà se essa compare tra le keyword pericolose in base ai contesti selezionati.
Tuttavia tale soluzione considererebbe molte proprietà come trascurabili solo perchè, per esempio, la chiave e la keyword differiscono per una lettera.
Tali falsi negativi possono essere attenuati utilizzando la distanza di Levenshtein per verificare la similarità tra due stringhe. Tale distanza rappresenta il numero minimo di modifiche elementari che consentono di trasformare la prima stringa nella seconda, nel nostro caso la chiave della proprietà nella keyword fissata.

Consideriamo le due stringhe simili se il punteggio restituito è superiore ad una certa soglia.

Una volta fatto ciò consideriamo tutte le chiavi delle proprietà non individuate come pericolose.
Nonostante la chiave non sia stata rilevata come simile ad una delle keyword sensibili, è possibile che il contenuto associato ad essa lo sia. 

Per verificare tale circostanza prendiamo in esame il contesto "health" o salute.

Ogni decisione presa dal processo di NER è una predizione basata sui valori pesati del modello. Tali valori sono stimati dagli esempi su cui il modello è stato allenato.
L'allenamento è un processo in cui le predizioni del modello sono comparate con gli esempi in modo da stimare il gradiente della perdita (gradient of loss). Tipicamente servono un centinaio di esempi per allenare e valutare il modello.

Associamo ad esso un modello di Spacy che esegua la NER (Named-Entity Recognition) con le categorie personalizzate di "PATHOGEN", "MEDICINE" e "MEDICALCONDITION". Questo modello è stato allenato con una serie di frasi con le annotazioni delle tre categorie sopra citate.
In questo modo se vengono rilevate delle entità, nel nostro caso quindi se vengono rilevate dei medicinali, dei patogeni o delle condizioni mediche, consideriamo l'intero valore della proprietà come pericoloso in quanto contiene plausibilmente delle informazioni mediche sensibili.
Tale verifica risulta tuttavia onerosa da eseguire su tutti i valori distinti di tutte le proprietà non considerate pericolose, a causa di proprietà con valori numerici o con alta numerosità nel dataset.
Vengono quindi considerati k valori distinti per ogni proprietà con la loro numerosità, n, e se la numerosità totale dei valori considerati pericolosi dalla NER supera una certa soglia, allora tutta la proprietà viene considerata come pericolosa.

Combinando queste due tecniche si ottiene una valutazione più accurata della pericolosità delle proprietà per il contesto "health".

Tecniche di sanitizzazione adottate
\textbf{
Una volta identificate le chiavi delle proprietà che rappresentano i dati sensibili per i contesti indicati, è ora necessario passare alla sanitizzazione. La scelta di quale delle tecniche implementate utilizzare è demandata all'utilizzatore del tool in quanto ogni strategia ha i suoi vantaggi e svantaggi da tenere in considerazione.
}
\textbf{
La prima tecnica di sanitizzazione proposta è la cancellazione di ogni proprietà rilevata come pericolosa.
Questa è da una parte la tecnica più sicura, in quanto non reversibile, ma l'eliminazione potrebbe far perdere una porzione elevata del database.
}
\textbf{
Una seconda strategia per la sanitizzazione è quella di utilizzare una cifratura simmetrica sui valori delle proprietà rilevate come pericolose.
}
% DA SPIEGARE
\textbf{ 
Per la cifratura simmetrica abbiamo deciso di utilizzare AES-256 ...
}
Per la cifratura verranno generate due chiave che poi verranno restituite all'utilizzatore così da poter effettuare eventualmente la decodifica.
Operativamente sarà necessario fare una query per richiedere tutti i valori per tutte le proprietà considerate pericolose, applicare la cifratura per ogni valore la cifratura (con le stesse chiavi) e salvare il contenuto cifrato composto dal nonce + tag + cyphertext.
\textbf{
Questa operazione è chiaramente molto costosa nel caso di proprietà con un alta numerosità e quindi potrebbe richiedere un costo computazionale e temporale notevole.
Questa tecnica permette di pubblicare in chiaro la chiave delle proprietà ma senza rilevarne il valore, che spesso rappresenta proprio il dato sensibile. Il proprietario dei dati, possedendo entrambe le chiavi necessarie per la decodifica, potrà ottenere nuovamente i valori iniziali delle proprietà.
Questo approccio è più adatto alla pubblicazione tramite API del database.
}

Un ulteriore strategia per la sanitizzazione combina le due tecniche precedenti, cancellando una parte delle proprietà e cifrandone la restante, con la specifica che o la totalità della proprietà viene cancellata o viene cifrata.
Considerando infatti il possibile alto costo computazione richiesto per cifrare tutte le proprietà ritenute pericolose, si definisce una soglia di soppressione che rappresenta la percentuale del nostro database che siamo disposti a cancellare in modo irreversibile. 
Possono capitare diversi scenari in base alla numerosità totale delle proprietà pericolose.
Il caso più semplice è quello in qui cancellando tutte le proprietà pericolose, non supereremmo la soglia fissata.
In un caso più generale invece consideriamo ogni proprietà pericolosa con la sua numerosità.
Attraverso un algoritmo greedy ricaviamo il sottoinsieme delle proprietà da cancellare e per complemento quelle da codificare.
Ordiniamo le proprietà in maniera decrescente in base alla loro numerosità, in modo che scorrendo la lista si scelga sempre quella con maggior numerosità
Se le occorrenze sommate alle occorrenze delle proprietà gia selezionate per l'eliminazione non superano la soglia, allora aggiungiamo la proprietà fissata tra quelle da eliminare. 
In questo modo selezioneremo il minor numero di proprietà da eliminare ma allo stesso tempo massimizzando la cancellazione fino alla soglia.