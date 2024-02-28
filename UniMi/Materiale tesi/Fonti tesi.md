Tesi stud boccioni [https://spdp.di.unimi.it/papers/lov-cn2023.pdf]
Guida per le label [https://neo4j.com/developer/kb/how-to-get-a-high-level-inventory-of-objects-in-your-graph/]
Generatore pazienti [https://github.com/synthetichealth/synthea/wiki/Basic-Setup-and-Running]
Pole Dataset [https://github.com/neo4j-graph-examples/pole/tree/main]
Articolo interessante [https://memgraph.com/blog/handling-large-graph-datasets]
Repo con dataset [https://networkrepository.com/soc.php]
- https://networkrepository.com/soc-livejournal.php

Altri dataset [https://ucsd.libguides.com/data-statistics/finddata]
altri esempi ufficiali [https://github.com/neo4j-graph-examples]

```cypher
MATCH (a) 
UNWIND keys(a) AS key
RETURN collect(distinct key)
```

Generazione sample [https://github.com/iansrobinson/graph-databases-use-cases]
Formula per creazione db da excel [https://towardsdatascience.com/getting-started-with-neo4j-in-10-minutes-94788d99cc2b]
Profiling [https://neo4j.com/blog/data-profiling-holistic-view-neo4j/]
Performance Python [https://neo4j.com/docs/python-manual/current/performance/]

```python
numbers = [{"value": random()} for _ in range(10000)]
driver.execute_query("""
    WITH $numbers AS batch
    UNWIND batch AS node
    MERGE (n:Number)
    SET n.value = node.value
    """, numbers=numbers,
)
```

[https://www.mockaroo.com/]
[https://faker.readthedocs.io/en/master/]