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

Vantaggi: `adatta un oggetto aderente a una interfaccia e NON una classe` quindi adatta tutta una gerarchia di classi

Svantaggi: sono due oggetti distinti a run time