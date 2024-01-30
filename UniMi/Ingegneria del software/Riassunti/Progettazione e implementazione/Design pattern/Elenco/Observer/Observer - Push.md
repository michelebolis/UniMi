In questo caso l’argomento Observable di `update` viene messo nullo, mentre `nell’Object viene passata la totalità dello stato del Subject`:

```java
// Observable ù
@Override 
public void notifyObservers() {      
	for (Observer observer : observers) {         
		observer.update(null, state);     
	}  
}  
// Observer 
@Override 
public void update(Observable model, Object state) {      
	if (state instanceof Integer intValue) {
	    doSomethingOn(intValue);     
	}  
}
```

Come si vede, dovendo definire come reagire al cambiamento di stato in `update` l’Observer dovrà innanzitutto fare un down-casting per ottenere un oggetto della classe corretta. Avendo la responsabilità di tale casting l’Observer dovrà conoscere precisamente la struttura dello stato del Subject, creando una _forte dipendenza_ che potrebbe creare problemi di manutenibilità.

Un altro problema di questo approccio è che gli Observer sono solitamente interessati a una piccola porzione dello stato del Subject, quindi passarlo tutto come parametro potrebbe sovraccaricare inutilmente la memoria.