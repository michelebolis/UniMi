- Combining knowledge- and data-driven methods for de-identification of clinical narratives

Abstract : La recente promessa di accedere ai dati clinici non strutturati delle cartelle cliniche elettroniche su larga scala ha rivitalizzato l'interesse per la de-identificazione automatica delle note cliniche, che comprende l'identificazione delle menzioni di informazioni sanitarie protette (PHI).

Riassunto
La de-identificazione di dati non strutturati rappresenta una sfida, in quanto le informazioni personali possono apparire praticamente ovunque in un racconto clinico.
Questo compito è spesso risolto con una NER denominate (Named Entity Recognition, NER), dove vengono menzionati specifici tipi di dati PHI 
L'identificazione automatica dei documenti non strutturati è un argomento di ricerca da più di vent'anni.
Da allora, sono stati introdotti numerosi sistemi, tra cui quelli knowledge-based, data-driven, nonché metodi ibridi che combinano vari approcci.
Viene rilevato come il risultato di una tokenizzazione non corretta, è principalmente una conseguenza diretta di problemi di qualità dei dati con i documenti forniti

- An AI framework to support decisions on GDPR compliance

Abstract : L'obiettivo principale di questo lavoro è quello di progettare un framework che possa essere efficacemente adottato per verificare se i documenti della PA scritti in italiano soddisfano i requisiti del GDPR.

Riassunto
Storia del GDPR
L'autorità per la protezione dei dati (DPA) di ogni Stato membro dell'UE - l'autorità pubblica indipendente che supervisiona l'applicazione del GDPR - emana sanzioni severe ai trasgressori, sia pubblici che privati.
Si concentrano sulle implicazioni del GDPR sulla pubblicazione di documenti non strutturati (testuali) che potrebbero rivelare informazioni personali.
Le tecniche di intelligenza artificiale, come l'elaborazione del linguaggio naturale (NLP), possono aiutare a rilevare automaticamente le parti dei documenti testuali che potrebbero costituire una violazione dei dati.
L'NLP è una sottoarea dell'IA che elabora il linguaggio umano naturale.

- Viewing the GDPR through a de-identification lens: a tool for compliance, clarification, and consistency

Riassunto
Nel maggio 2018, il Regolamento generale sulla protezione dei dati (GDPR) è entrato in vigore come legge sulla protezione dei dati nello Spazio economico europeo (SEE).
La de-identificazione può essere complessa da un punto di vista tecnico, ma non c'è dubbio che le tecniche di de-identificazione, correttamente applicate, possono ridurre i rischi per la privacy e contribuire a proteggere i diritti fondamentali degli interessati.
Vari metodi di de-identificazione includono forme di mascheramento, soppressione, trasformazione o campionamento dei dati.
(disamina legale del gdpr)

- The Property Graph Database Model

Abstract : Il presente documento presenta una definizione formale del modello di database a grafo di proprietà. In particolare, viene descritta la struttura dei dati del grafo, le nozioni di base dei vincoli di integrità (ad esempio lo schema del grafo) e un linguaggio di interrogazione del grafo.

Riassunto
Informalmente, un grafo delle proprietà è un multigrafo etichettato diretto con la caratteristica speciale che ogni nodo o bordo può mantenere un insieme (eventualmente vuoto) di coppie proprietà-valore.

![[Pasted image 20240521102617.png]]

- Demystifying Graph Databases: Analysis and Taxonomy of Data Organization, System Designs, and Graph Queries

Abstract : Numerosi insiemi di dati di grafi irregolari, ad esempio reti sociali o grafi web, possono contenere anche trilioni di edge. Spesso la loro struttura cambia nel tempo e hanno dati ricchi specifici per il dominio associati a vertici e edge. I sistemi di database a grafi, come Neo4j, consentono di memorizzare, elaborare e analizzare tali insiemi di dati ricchi e in evoluzione. Ci concentriamo sull'identificazione e sull'analisi delle categorie fondamentali
di questi sistemi, i modelli di grafi associati e le tecniche di organizzazione dei dati.

Riassunto
I database a grafo (GDB), come Neo4j, sono emersi per consentire l'archiviazione, l'elaborazione e l'analisi di insiemi di dati a grafo di grandi dimensioni, in continua evoluzione e ricchi di informazioni.
Un grafo $G$ puo essere modellato come una tupla $(V, E)$ dove 
- $V$ è l'insieme dei nodi 
- $E \subseteq V \times V$ è l'insieme degli archi 

Considerando il grafo come orientato, un arco $e = (u, v) \in E$ è composto da due nodi, $u$ nodo "mittente"/uscente e $v$ nodo "destinazione"/entrante.
I database che adottano un modello Labeled Property Graph, aggiungono dei componenti alla definizione di grafo. Infatti ogni nodo o arco puo essere etichettato e contenere un insieme, eventualmente vuoto, di proprietà definite da una coppia (chiave, valore).
In particolare un LPG è una tupla $G = (V, E, L, I_V, I_E, K, W, p_V, p_E)$ dove
- $L$ è l'insieme delle etichette
- $I_V : V \mapsto P(L)$ e $I_E : E \mapsto P(L)$ sono funzioni di etichettatura rispettivamente di nodi e archi con $P(L)$ che denota tutti i possibili sottoinsiemi di $L$
- $K$ è l'insieme delle possibili chiavi delle proprietà
- $W$ è l'insieme dei possibili valori delle proprietà
- $p_V : V \mapsto K \times W$ denota l'insieme delle coppie (chiave, valore) che rappresenta l'insieme delle proprietà definite nel nodo fissato
- $p_E : E \mapsto K \times W$ denota l'insieme delle coppie (chiave, valore) che rappresenta l'insieme delle proprietà definite nell'arco fissato

Neo4j nello specifico adotta un modello Labeled Property Graph ma permettendo di etichettare un arco, chiamato relazione, con una sola etichetta, chiamata tipo (type).

- Collective Data-Sanitization for Preventing Sensitive Information Inference Attacks in Social Networks

Abstract: Sfortunatamente, le informazioni sensibili possono essere predette dai dati rilasciati  
attraverso le tecniche di data mining. Pertanto, e necessario sanificare i dati prima  
di rilasciarli. Le tecniche di conservazione della privacy esistenti, come la privacy  
differenziale, il k-anonimizzazione e la l-diversita sono progettate solo per la privacy  
dei dati intrinseci, e non proteggono direttamente dagli attacchi di inferenza.  
Gli attributi possono essere manipolati in tre modi: aggiungendo nuovi attributi,  
rimozione quelli esistenti e perturbazione (sostituzione di un attributo con un altro).  
Poich ́e sia l’aggiunta che la perturbazione riducono l’accuratezza della previsione sulle  
informazioni sensibili, introducendo diversi tipi di rumori, essi sono chiamati collet-  
tivamente metodo di offuscamento. La rimozione, invece, puo essere vista come un  
metodo di anonimizzazione.  
Tuttavia la scelta di quale tecnica utilizzare e direttamente legata al tipo di data-  
base e allo scopo associato alla sua pubblicazione. In alcuni casi, il metodo di pertur-  
bazione potrebbe essere una scelta appropriata in quanto puo garantire il desiderato  
compromesso privacy-utilita.

- Privacy in Microdata Release: Challenges, Techniques, and Approaches

Abstract: viviamo sempre di piu in una società che si basa sulla disponibilità di informazioni per prendere delle decisioni. Ci sono molti benefici associati ma allo stesso tempo ci sono  molte leggi e regolamentazioni che riconoscono la privacy e la protezione dei dati come un diritto. Inizialmente i dati venivano rilasciati sotto forma di statistiche aggregate (macrodata) ma cio era molto limitante per l'utilizzatore, quindi per garantire una maggiore flessibilità, si rilasciano dati dettagliati (microdata). Il problema è chiaramente che, in termini di protezione dei dati, i microdata potrebbero contenere informazioni sensibili

Tecniche di protezione
La comunità scientifica ha proposto diverse tecniche per la protezione dei microdata.
Distinguiamo tra le tecniche di masking e le tecniche di syntetic data generation.
Le prime operano direttamente sui microdata originali per sanitizzarli prima del loro rilascio mentre le seconde prevedono il rilascio di un nuovo dataset che mantenga alcune proprietà statistiche dei dati originali.
Le tecniche di masking possono essere classifiche come
- Non perturbative: non modificano direttamente i dati originali ma rimuovono dettagli dalla tabella, sacrificando data completeness. Questa categoria include la soppressione, la generalizzazione e il bucketization. La soppressione rimuove informazioni dalla tabella. La generalizzazione sostituisce selettivamente il contenuto di alcune celle con un valore piu generico, spesso basato su gerarchie di generalizzazione. Il bucketization opera su set di attributi la cui unione dovrebbe essere evitata dividendo le tuple in bucket, mischiandole all interno del bucket in modo da rompere la corrispondenza
- Perturbative: distorcono le tabelle da rilasciare modificando il loro contenuto informativo, sacrificando data truthfulness. Esempi di queste tecniche sono l'aggiunta di rumore e la microaggregazione. La prima tecnica aggiunge valori alla collezione di dati iniziali in questo modo alcuni valori inclusi in quelli rilasciati non corrisponderanno a quelli veri e vice versa. La microaggregazione invece rimpiazza selettivamente tuple originali con alcune nuove, prima raggrupando le tuple in gruppi in modo che le tuple dello stesso gruppo siano simili, e poi rimpiazzando con un valore restituito da un operatore di aggregazione (es media)

Un importante osservazione è che tutte le tecniche di protezione di microdata prevedono la perdita di informazioni. Per questo la comunità scientifica ha proposto degli approcci di protezione che, dato un requisito di privacy da soddisfare, si affidano alle tecniche sopra citate limitando la perdita di informazioni.

Le tecniche tradizioni di protezione dei microdata sono costruite sull'assunzione che i dati da rilasciare si trovino su una singola tabella. Questo rappresenta una limitazione in molti scenari reali o in una rappresentazione non tabellare.

- k-Anonymity: From Theory to Applications

Abstract: k anonymity è un modello di privacy pensato per proteggere le identità degli individui coinvolti nella pubblicazioni della collezioni di dati.

Social Network Analysis
I dati di un social network sono solitamente rilasciati sotto forma di grafo, dove i nodi rappresentano gli utenti mentre gli archi le relazioni tra essi.
La semplice rimozione delle identità degli utenti dai nodi non fornisce alcuna garanzia sull'anonimizzazione. Per rispettare una metrica di protezione, sono necessarie modifiche alla struttura del grafo, quali aggiunta/cancellazione di nodi/archi.
Una prima possibilità è quella di applicare queste modifiche in modo casuale in modo da fornire una resistenza probabilistica alla ridentificazione.
Altre soluzioni si basano su k-anonymity per offrire una quantificazione della protezione contro la ridentificazione. 
L'assunzione in questo contesto è che il grado dei nodi è considerato un quasi-identificatore. Si è proposta la nozione di k-degree anonymity richiedendo che ogni nodo abbia lo stesso grado di almeno k-1 nodi del grafo
Un altro requisito di privacy proposto si basa sull'assunzione che sia possibile identificare nuovamente un utente grazie alla struttura del grado. Si propone la nozione di k-neighborhood anonymity che richiede che il 1-neighborhood sottografo sia isomorfo a quello di almeno k-1 nodi

- https://www.oracle.com/it/big-data/structured-vs-unstructured-data/