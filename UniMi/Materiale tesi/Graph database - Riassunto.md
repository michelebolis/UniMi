Capitolo 1
Un `labeled property graph` è formato da nodi collegati da relazioni
Ogni nodo ha una o piu `label` che indicano il suo ruolo.
Ogni nodo ha delle `proprietà` (chiave-valore) come anche le relazioni.
Ogni relazione finisce ed inizia in un nodo

Capitolo 2

Capitolo 3
Cypher
```cypher
MATCH (a:Person {name:'Jim'})-[:KNOWS]->(b)-[:KNOWS]->(c), (a)-[:KNOWS]->(c) RETURN b, c
```

- `MATCH` 
Usiamo `<` e `>` per indicare la direzione della relazione, che indichiamo con `-`
```cypher
MATCH (nodo1 {keyProprierta:valoreProprieta})-[:TipoRelazione]->(nodo2)
```

- `WHERE`
```cypher
MATCH (nodo1)-[:TipoRelazione]->(nodo2)
WHERE nodo1.keyProprierta = valoreProprieta
```

- `CREATE/CREATE UNIQUE`: crea nodi e relazioni
	- Creazione di un nodo con delle property
	```cypher
	CREATE (shakespeare:Author {first name:'William', lastname:'Shakespeare'})
	```
	- Creazione di una relazione
	```cypher
	(shakespeare)-[:WROTE_PLAY {year:1599}]- >(juliusCaesar)
	```
	- Creazione di un indice (per ottimizzazione nella ricerca)
	```cypher
	CREATE INDEX ON :Venue(name)
	```
	- Creazione di un constraint
	```cypher
	CREATE CONSTRAINT ON (c:Country) ASSERT c.name IS UNIQUE
	```

- `MERGE`:  il pattern esplicitato se non esiste, ma è possibile che ci sia creando nuove relazioni o nodi
- `DELETE`: cancella nodi/relazioni/proprietà
- `SET`: setta le proprietà
- `FOREACH`: update su tutti gli elementi di una lista
- `UNION`: merge ii risultati di piu query
- `WITH`: mette in sequenza parti della query passando alla successiva parte il risultato della prima (simile al piping)

Esempio
```cypher
MATCH (bard:Author {lastname:'Shakespeare'})-[w:WROTE_PLAY]->(play) 
WITH play 
ORDER BY w.year DESC 
RETURN collect(play.title) AS plays
```

- `START` (deprecato) 
- `RETURN/RETURN DISTINCT`
- `ORDER BY`

Match avanzati
- `[*n..k]` indica che ci possono essere come minimo n relazioni e al massimo k che collegano i nodi
```cypher
MATCH (user:User)-[*1..5]-(asset:Asset)
```
- Nodi anonimi
```cypher
(()-[:PERFORMANCE_OF]->())
```
- Conteggio
```cypher
RETURN count(p)
```
- Lista degli elementi
```cypher
RETURN collect(play.title) AS plays
```
- Conteggio dei path possibili
```cypher
MATCH (email:Email {id:'11'})<-[f:FORWARD_OF*]-(:Forward) 
RETURN count(f)
```


Capitolo 4
Nodi = cose del nostro dominio
Relazioni = contesto semantico
Proprieta dei nodi = attributi delle entita
Proprieta delle relazioni = peso/forza/qualita della relazione

Importing e Bulk Loading (pagina 118)
```cypher
neo4j-import --into target_directory \ --nodes movies.csv --nodes actors.csv --relationships roles.csv
```

Capitolo 5
Use cases
- Social
- Recommendations
- Geospatial
- Master Data Management
- Network and Data Center Management
- Authorization and Access Control