1. Cosa si intende per private/sensibile?
the presence of sensitive information was detected using lists of sensitive terms associated by taking inspiration from the definition of sensitive data in the EU GDPR – with ten sensitive information categories that include: (i) health status, (ii) ethnicity, (iii) religion, (iv) political affiliation, (v) sexual orientation, (vi) geolocation, (vii) profession, (viii) marital status, (ix) interests/passions, and (x) age. 
We note that the first five categories represent special category personal data according to Art. 9 of the EU GDPR, and are therefore deemed highly sensitive and in need of specific protection, unlike the remaining categories that we denoted as less sensitive. Lists of sensitive terms for each category have been taken from (health status), (ethnicity), (religion), [16] (profession), [27] (political affiliation), [1] (sexual orientation), [13] (geolocation), [10] (marital status), [20] (interests/passions).
Fonte: Tesi 

The following personal data is considered ‘sensitive’ and is subject to specific processing conditions:
- personal data revealing racial or ethnic origin, political opinions, religious or philosophical beliefs;
- trade-union membership;
- genetic data, biometric data processed solely to identify a human being;
- health-related data;
- data concerning a person’s sex life or sexual orientation.
Fonte: [https://commission.europa.eu/law/law-topic/data-protection/reform/rules-business-and-organisations/legal-grounds-processing-data/sensitive-data/what-personal-data-considered-sensitive_en]

==I dati dell'azienda NON sono di competenza del GDPR==
es cellulare della pizzeria NO
es cellulare aziendale del dipendente SI
Fonte [https://commission.europa.eu/law/law-topic/data-protection/reform/rules-business-and-organisations/application-regulation/do-data-protection-rules-apply-data-about-company_en]

ART 4 GDPR
«dato personale»: qualsiasi informazione riguardante una persona fisica identificata o identificabile («interessato»); si considera identificabile la persona fisica che può essere identificata, direttamente o indirettamente, con particolare riferimento a un identificativo come il nome, un numero di identificazione, dati relativi all'ubicazione, un identificativo online o a uno o più elementi caratteristici della sua identità fisica, fisiologica, genetica, psichica, economica, culturale o sociale;

ART 9 GDPR
È vietato trattare dati personali che rivelino l'origine razziale o etnica, le opinioni politiche, le convinzioni religiose o filosofiche, o l'appartenenza sindacale, nonché trattare dati genetici, dati
Eccezioni
a) consenso
e) ==il trattamento riguarda dati personali resi manifestamente pubblici dall'interessato==
Fonte: [https://www.garanteprivacy.it/documents/10160/0/Regolamento+UE+2016+679.+Arricchito+con+riferimenti+ai+Considerando+Aggiornato+alle+rettifiche+pubblicate+sulla+Gazzetta+Ufficiale++dell%27Unione+europea+127+del+23+maggio+2018.pdf/1bd9bde0-d074-4ca8-b37d-82a3478fd5d3?version=1.9]

Problema principale: individuare "contesto" e l'entita in questione --> E' una persona?
Per individuare le entita: [https://cloud.google.com/natural-language/?hl=it]

2. Come individuiamo nel db cosa è sensibile?
Profiling db prendendo tutte le label, tutte le properties key e i tipi di relazioni
Profiling [https://neo4j.com/blog/data-profiling-holistic-view-neo4j/]

```cypher
MATCH (a) 
UNWIND keys(a) AS key
RETURN collect(distinct key)
```

3. Che metriche posso utilizzare per valutare il db?
cose che posso fare:
- raffinare statistiche (di quegli archi, quanti in ingresso/uscita/ con quale label)
- topologia grafo
	- centralità del nodo 
	- outlier: 
		- nodo mail 9/10 è collegato a uni e solo 1/10 a persona 
		- nodi non etichettati

| Node Risk           | Warning label         | No Warning label      |
| ------------------- | --------------------- | --------------------- |
| Warning property    | RISK                  | look at relationships |
| No Warning property | look at relationships | NO RISK               |

| Relationship Risk   | Warning label | No Warning label                                                |
| ------------------- | ------------- | --------------------------------------------------------------- |
| Warning property    | RISK          | risk if it is connected to a risk label                         |
| No Warning property | ??            | risk if it connects a risk label with a node with risk property |

Possibile algoritmo
```
spots = given the warning properties, find all the nodes where (labels) they are
no context = given the warning properties, the nodes where they are have no label

if label is sensibile
	count = conteggio nodi con quella label
	for node in isolated node
		if label == node.label
			suggest to erase node
			cont -= 1
	found = False
	for property in warning properties
		if property[label] : found = True
	if not found : 
		if are there out/in relationships from/to spots :
			# label sensibile collegate a nodi con propieta sensibili MA non ha proprieta pericolose
			??
		else :
			# label sensibile MA non ha proprieta pericolose e non è collegate a proprieta pericolose
			# Falso allarme ?
			NO WARNING ?
else
	found = False
	for property in warning properties
		if property[label] : found = True
	if not found : 
		# Non è una label pericolosa e non ha properieta pericolose
		NO WARNING
	else 
		if label is a person : 
			HIGH WARNING
			if is the central node : 
				suggest to erase warning properties IF are not public info
		else : NO WARNING ?
```


4. Che suggerimenti posso dare per ridurre il pericolo?
	- Cancellazione
	- Generalizzazione
	- Anonimizzazione [https://mostly.ai/blog/data-anonymization-in-python]
5. Dataset? [https://neo4j.com/docs/graph-data-science/current/management-ops/graph-creation/graph-generation/]
Generatore pazienti [https://github.com/synthetichealth/synthea/wiki/Basic-Setup-and-Running]
Generazione sample [https://github.com/iansrobinson/graph-databases-use-cases]
Pole Dataset [https://github.com/neo4j-graph-examples/pole/tree/main]
Generazione sample (limitato a 1k) [https://www.mockaroo.com/]
Package di python utilizzabile per la generazione del sample [https://faker.readthedocs.io/en/master/]
Formula per creazione db da excel [https://towardsdatascience.com/getting-started-with-neo4j-in-10-minutes-94788d99cc2b]
Altri dataset [https://ucsd.libguides.com/data-statistics/finddata]
altri esempi ufficiali [https://github.com/neo4j-graph-examples]
Repo con dataset [https://networkrepository.com/soc.php]
- https://networkrepository.com/soc-livejournal.php
