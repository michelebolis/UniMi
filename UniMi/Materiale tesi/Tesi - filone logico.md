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

