```scala
def get[A, B](key: A): Option[B] = { 
	if (contains(key)) new Some(getValue(key)) 
	else None 
}
```

Le Option sono utilizzate per integrare funzioni e oggetti