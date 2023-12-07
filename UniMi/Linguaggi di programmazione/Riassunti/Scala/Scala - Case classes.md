```scala
abstract class Bool { 
	def and(b: => Bool): Bool 
	def or(b: => Bool): Bool 
} 
case object True extends Bool {
	def and(b: => Bool) = b 
	def or(b: => Bool) = this 
} 
case object False extends Bool { 
	def and(b: => Bool) = this 
	def or(b: => Bool) = b 
} 
def bottom: () => Nothing = () => bottom()
```

```cmd
:load short-circuit.scala
True and bottom() // java.lang.StackOverflowError
True or bottom() // object True = True
```

Data la classe astratta Bool, si decide quale object (quale istanza singola) utilizzare in base al case 