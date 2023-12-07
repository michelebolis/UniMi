I traits  preservano la separazioni di concetti delle interfacce mentre permettono di comporre comportamenti (come interfaccia con implementazione MA non è instanziabile e NON vi è un vincolo di classe-sottoclasse)

Vengono utilizzati nelle altre classi con `with nomeTrait`

es Observer
```scala
class Button(val label: String) { 
	def click() = { /*...*/ }
}
trait Subject { 
	type Observer = { def receiveUpdate(subject: Any) } 
	private var observers = List[Observer]() 
	def addObserver(observer:Observer) = observers ::= observer
	def notifyObservers = observers foreach (_.receiveUpdate(this)) 
}

class ButtonCountObserver { 
	var count = 0 
	def receiveUpdate(subject: Any) = count += 1
}
class ObservableButton(name: String) extends Button(name) with Subject {
	override def click() = { super.click() notifyObservers } 
}
object ButtonObserverTest { 
	def main(args: Array[String]) = { 
		val observableButton = new ObservableButton("Okay") 
		val buttonObserver = new ButtonCountObserver 
		observableButton.addObserver(buttonObserver) 
		for (i <- 1 to 3) observableButton.click() 
		printf("The button has been clicked %d times\n", buttonObserver.count) 
	}
}
```

Si puo sostituire la `class ObservableButton` con
```scala
val observableButton = new Button("Okay") with Subject { 
	override def click() = { super.click() notifyObservers } 
}
```

```cmd
scala ButtonObserverTest
The button has been clicked 3 times
```

[[Scala - Stackable Traits]]