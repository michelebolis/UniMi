Diversi trait possono essere impilati sulla stessa classe
```scala
trait Clickable { def click() }
class Button(val label: String) extends Clickable { 
	def click() = { /* Logic to give the appeareance of clicking a button... */ } 
}
trait Subject { 
	type Observer = { def receiveUpdate(subject: Any) } 
	private var observers = List[Observer]() 
	def addObserver(observer:Observer) = observers ::= observer
	def notifyObservers = observers foreach (_.receiveUpdate(this)) 
}

trait ObservableClicks extends Clickable with Subject { 
	abstract override def click() = { super.click() notifyObservers } 
}
```

In `ObservableClicks`, `super.click()` non fa riferimento NE a Clickale NE a Subjest MA sarà sarà legato quando il trait sarà legato

```scala
trait VetoableClicks extends Clickable { 
	val maxAllowed = 1 // default 
	private var count = 0 
	abstract override def click() = { 
		if (count < maxAllowed) { count += 1; super.click() } 
	} 
}

object ButtonClickableObserverTest { 
	def main(args: Array[String]) = {
		val observableButton = new Button("Okay") with ObservableClicks with VetoableClicks
		val buttonClickCountObserver = new ButtonCountObserver 
		observableButton.addObserver(buttonClickCountObserver) for (i <- 1 to 3) 
		observableButton.click() printf("The button has been clicked %d times\n", buttonClickCountObserver.count) 
	} 
}
```

I trait vengono risolti da destra verso sinistra

```cmd
scala ButtonObserverTest
The button has been clicked 1 times
```

I trait NON supportano costruttori ausiliari 
Possono estendere classi o altri trait MA non possono passargli argomenti, quindi possono estendere classi/trait con costruttore che non richiede argomenti
I trait sono eseguiti ogni volta che un istanza che usa il trait è creata

[[Scala - Es Traits]]