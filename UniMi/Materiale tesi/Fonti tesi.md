Tesi stud boccioni [https://spdp.di.unimi.it/papers/lov-cn2023.pdf]
- Analisi dataset
Guida per le label [https://neo4j.com/developer/kb/how-to-get-a-high-level-inventory-of-objects-in-your-graph/]
Articolo interessante [https://memgraph.com/blog/handling-large-graph-datasets]

Performance Python [https://neo4j.com/docs/python-manual/current/performance/]

Como consigliato per eseguire query
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
