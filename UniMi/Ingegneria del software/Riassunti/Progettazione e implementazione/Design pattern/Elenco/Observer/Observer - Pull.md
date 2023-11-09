Con questo approccio, invece di mandare lo stato all’`update` **viene passato il Subject stesso**, il quale conterrà uno o più metodi per accedere allo stato (`getState`):

```java
// Observable 
@Override 
public void notifyObservers() {      
	for (Observer observer : observers) {
	     observer.update(this, null);     
	}  
}  
// Observer 
@Override 
public void update(Observable model, Object state) {      
	if (model instanceof ConcreteObservable cModel) {
	     doSomethingOn(cModel.getState());     
	}  
}
```

Sebbene comporti un passaggio in più poiché l’Observer deve chiamare un metodo del Subject quando riceve la notifica, questo cambio di prospettiva offre due vantaggi: in primo luogo non viene passato tutto lo stato, il che fa risparmiare molta memoria; inoltre, il Subject potrebbe decidere di rendere disponibili sottoinsiemi diversi dello stato con getter diversi, mostrando così ad ogni Observer solo le informazioni per esso rilevanti.

Inoltre, sebbene anche in questo caso sia richiesto un casting (da Observable al Subject), questo approccio rende meno dipendenti dalla rappresentazione interna del Subject: fintanto che la firma dei getter non cambia lo stato interno del Setter può cambiare senza problemi.