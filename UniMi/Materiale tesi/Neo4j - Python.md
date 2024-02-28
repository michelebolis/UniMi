```python
records, _, _ = driver.execute_query(
	""" 
	MATCH (p:Person)-[:ACTED_IN]->(m:Movie) 
	WHERE m.title = $title 
	RETURN p.name AS name LIMIT 10 
	""", title=title)
```