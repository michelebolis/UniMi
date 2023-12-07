- Unapply
Usato per estratta la parte consistente da un'istanza

```scala
object Twice { 
	def unapply(z: Int): Option[Int] = 
		if (z%2 == 0) Some(z/2) else None } 
object TwiceTest extends Application { 
	val x = 42; x match { case Twice(n) => Console.println(n) } 
}
```

```cmd
TwiceTest
21
```


- Apply
Usato per creare una collezione da una lista di argomenti variabili o estrarre i primi elementi di una collezione

```scala
object L2 { 
	def unapplySeq(s: String) : Option[List[String]] = 
		Some(s.split(",").toList) 
	def apply(stuff: String*) = stuff.mkString(",") 
}
```

```cmd
val x2 = L2("4","5","6") //uso l'apply
x2: String = 4,5,6

val L2(d,e,f) = x2 
d: String = 4 
e: String = 5 
f: String = 6
```