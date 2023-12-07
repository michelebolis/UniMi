Comprehension: dato un set voglio computarlo e estrarre qualcosa di nuovo
```scala
def sum_evens = (L:List[Int]) => {var sum=0; for (X <- L if X%2 == 0) sum += X; sum}
```
Generators (Yielding): data una comprehension, ottenere una nuova collection
```scala
val is_prime = (X:Int) => { 
	val divisors = (X:Int) => 
		for { Y <- List.range(2, math.sqrt(X).toInt) 
		if (X % Y == 0)} yield Y divisors(X).length == 0 }
```