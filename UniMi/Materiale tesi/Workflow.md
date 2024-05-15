1. Creazione parametri framework

```demo
driver := contiene il punto di accesso alla base di dati
keyword_context_node := contiene i contesti e le relative keyword da utilizzare nei nodi
keyword_context_rels := contiene i contesti e le relative keyword da utilizzare nelle relazioni tra nodi
ner_context_node := contiene i contesti da considerare in fase di ner nei nodi
ner_context_rels := contiene i contesti da considerare in fase di ner nelle relazioni
```

2. Creazione del framework 

```demo
framework := new Framework(driver, keyword_context_node, keyword_context_rels, ner_context_node, ner_context_rels)
```

```pseudocodice
__init__(driver, keyword_context_node, keyword_context_rels, ner_context_node, ner_context_rels) :
	self.driver := contiene il punto di accesso alla base di dati
	self.keyword_context_node := contiene i contesti e le relative keyword da utilizzare nei nodi
	self.keyword_context_rels := contiene i contesti e le relative keyword da utilizzare nelle relazioni tra nodi
	self.ner_context_node := contiene i contesti da considerare in fase di ner nei nodi
	self.ner_context_rels := contiene i contesti da considerare in fase di ner nelle relazioni
	self.models = contiene per ogni contesto, il modello ner da utilizzare e la lista di entita considerate pericolose
	self.aes_key := viene generata una chiave casuale aes per le sanitizzazioni con cifratura
	self.hmac_key := viene generata una chiave casuale hmac per le sanitizzazioni con cifratura
```

3. Getter delle informazioni della base di dati

```pseudocodice
getInfoFromDb() :
	self.countNodes := numero dei nodi nella base di dati
	self.countRelationships := numero di relazioni nella base di dati
	self.properties := lista di tutte le keyword distinte delle proprietà presenti nei nodi
	self.labels := lista di tutte le label distinte che etichettano dei nodi
	self.relationships := lista di tutti i tipi distinti di relazioni
	self.relationships_properties := lista di tutte le keyword distinte delle proprietà presenti nelle relazioni
	self.outgoing_relationships := contiene, per ogni label, tutte le sue relazioni uscenti da quel nodo e la loro numerosità
	self.ingoing_relationships := contiene, per ogni label, tutte le sue relazioni uscenti da quel nodo e la loro numerosità
	classifyProperties() 
```

```pseudocodice
classify_properties() :
	warning_properties := lista delle proprietà presenti nei nodi considerate pericolose dati i contesti (keyword_context_node) e le keyword associate a ciascuno 
	warning_properties_in_rel := lista delle proprietà presenti nelle relazioni considerate pericolose dati i contesti (keyword_context_rels) e le keyword associate a ciascuno 
	
	self.classified_properties_nodes := contiene per ogni label (in base alle warning_properties) la lista delle proprietà pericolose e la lista di quelle non pericolose, classificando poi ogni proprietà come "sempre presente" nei nodi con tali label o come "facoltativa"
	self.classified_properties_rels := contiene per ogni tipo di relazione (in base alle warning_properties_in_rel) la lista delle proprietà pericolose e la lista di quelle non pericolose, classificando poi ogni proprietà come "sempre presente" nelle proprieta di quel tipo o come "facoltativa"
```

4. Scelta del metodo di sanitizzazione da utilizzare per le keyword delle proprietà considerate pericolose

- sanitization_brutal_delete

```pseudocodice
sanitization_brutal_delete() :
	props_nodes := contiene per ogni label la lista delle keyword delle proprietà considerate pericolose nei nodi
	props_rels := contiene per ogni tipo la lista delle keyword delle proprietà considerate pericolose nelle relazioni
	delete_properties(props_nodes, props_rels)
```

```pseudocodice
delete_properties(props_nodes, props_rels) :
	for each label, properties_list in props_nodes :
		for each prop in warning_optional : 
			Rimuovo la proprietà da tutti i nodi con la label fissata
		IF non ci sono altre proprietà oltre a quelle pericolose nei nodi con la label fissata THEN
			Cancella i nodi con la label fissata
		ELSE : 
			for each prop in warning_always :
				Rimuovo la proprietà da tutti i nodi con la label fissata
	
	for each rel, properties_list in props_rels :
		for each prop in properties_list : 
			Rimuovo la proprietà da tutte le relazioni con il tipi fissato
```

- sanitization_encrypt

```pseudocodice
sanitization_encrypt() :
	for each label, warning_props in self.classified_properties_nodes :
		for each prop in warning_props :
			res := contiene per ogni nodo il suo id e il valore della proprietà fissata quando questa è presente in un nodo con la label fissata
			newvalues := contiene per ogni nodo il suo id e il nuovo valore cifrato utilizzando le chiavi aes_key e hmac_key generate precedentemente
			Aggiorno la proprietà con le informazioni presenti in newvalues
	for each rel, warning_props in self.classified_properties_rels :
		for each prop in warning_props :
			res := contiene per ogni relazione il suo id e il valore della proprietà fissata quando questa è presente in una relazione con il tipo fissato
			newvalues := contiene per ogni relazione il suo id e il nuovo valore cifrato
			Aggiorno la proprietà con le informazioni presenti in newvalues
```

- sanitization_faker

```

```

5. Scelta del metodo di sanitizzazione da utilizzare nella ner per le proprietà non considerate pericolose

```pseudocodice
sanitization_ner(not_warning, contexts, getterValues, getterIds, update, replace, blacklist) :
	not_warning := contiene la lista di coppie label/tipo, proprietà le cui chiavi sono considerate non pericolose dal modello  
	getterValues := funzione con cui ricavare i valori distinti della proprietà in nodi/relazioni con un dato label/tipo
	getterIds := funzione con cui ricavare gli id dei nodi/relazioni con un dato label/tipo in cui la proprietà fissata ha un dato valore
	update := funzione con cui aggiornare i valori della proprieta fissati in nodi/relazioni con un dato id
	replace := funzione con cui si ricava il nuovo valore dell'entita rilevata dalla ner
	blacklist := lista delle proprietà da ignorare 
	
	data := contiene per ogni coppia (label/tipo, proprietà) 
		- l'elenco delle entità rilevate con le corrispettive label
		- l'elenco dei valori distinti della proprietà originali
	for each prop, label in not_warning :
		if prop in blacklist : continue
		data[(prop, label)] = 
			[([], value) for value in getterValues(label, prop)]
	for each context, (model, entity_labels) in self.models :
		if context not in contexts : continue
		for each (prop, label), items in data :
			for each index, oldEnts, oldText in items :
				if item is numeric : continue
				ents := elenco delle entita utilizzando il modello attuale
				oldEnts.append(ents)
				items[index] = oldEnts, oldText
	for each prop, label, items in data:
		for each ents, oldText in items :
			if len(ents) == 0 : continue
			newText := valore aggiornato del valore (oldText) della proprieta (prop) utilizzando il metodo replace e le entità rilevate
			newvalues = []
			ids = getterIds(label, prop, newText)
			for each id in ids : 
				newvalues.append({"id" : id, "data" : newText})
			update(label, prop, newvalues)
```

- sanitization_ner_suppression

```pseudocodice
sanitization_ner_suppression(blacklist)
	ner_suppression := sostituisce il valore dell'entità con "*"
	sanitization_ner(not_warning, self.ner_context_node, getDistinctValulesNodes, getIdsNodes, updateValuesNodes, ner_suppression, blacklist)
	sanitization_ner(not_warning, self.ner_context_rels, getDistinctValulesRels, getIdsRels, updateValuesRels, ner_suppression, blacklist)
```

- sanitization_ner_encrypt

```pseudocodice
sanitization_ner_anonimize(blacklist)
	ner_encrypt := sostituisce il valore dell'entità con la cifratura di quest'ultima utilizzando le chiavi aes_key e hmac_key generate precedentemente
	sanitization_ner(not_warning, self.ner_context_node, getDistinctValulesNodes, getIdsNodes, updateValuesNodes, ner_encrypt, blacklist)
	sanitization_ner(not_warning, self.ner_context_rels, getDistinctValulesRels, getIdsRels, updateValuesRels, ner_encrypt, blacklist)
```

- sanitization_ner_anonimize

```pseudocodice
sanitization_ner_anonimize(blacklist)
	ner_anonimize := sostituisce il valore dell'entità con la label dell'entità rilevata
	sanitization_ner(not_warning, self.ner_context_node, getDistinctValulesNodes, getIdsNodes, updateValuesNodes, ner_anonimize, blacklist)
	sanitization_ner(not_warning, self.ner_context_rels, getDistinctValulesRels, getIdsRels, updateValuesRels, ner_anonimize, blacklist)
```

- sanitization_ner_faker

```pseudocodice
sanitization_ner_anonimize(fakers, blacklist)
	fakers := fornisce, per un elenco di label delle entità rilevabili dai modelli, una funzione che restituisce una stringa (il nuovo valore randomico)
	ner_faker := sostituisce il valore dell'entità con il valore restituito dal faker per quella label. SE non è fornito, allora lo sostituisce con un "*"
	sanitization_ner(not_warning, self.ner_context_node, getDistinctValulesNodes, getIdsNodes, updateValuesNodes, ner_faker, blacklist)
	sanitization_ner(not_warning, self.ner_context_rels, getDistinctValulesRels, getIdsRels, updateValuesRels, ner_faker, blacklist)
```

