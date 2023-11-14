Scenari
- usare uno o piu componenti ma non sono direttamente compatibili
- facendo evolvere incrementalmente un sistema mi ritrovo componenti vecchi che devono collaborare con quelli nuovi

Class Adapter
![[Pasted image 20231114162744.png]]
```java
public class Adapter extends Adaptee implements Target {
	@Override
	public void request(){
		this.oldRequest();
	}
}
```

Vantaggi
- E' un unico oggetto che puo essere usato contemporaneamente con le due interfaccie diverse
- SE un metodo cambia, non devo fare nulla

Svantaggi: possibili problemi con ereditarietà multipla

Object Adapter
![[Pasted image 20231114162800.png]]
```java
public class Adapter implements Target {
	private final Adaptee adaptee;
	public Adapter(Adaptee adaptee){
		asser adaptee != null;
		this.adaptee = adaptee;
	}
	@Override
	public void request(){
		adaptee.oldRequest();
	}
}
```

Vantaggi: adatta un oggetto aderente a una interfaccia e NON una classe quindi adatta tutta una gerarchia di classi

Svantaggi: sono due oggetti distinti a run time