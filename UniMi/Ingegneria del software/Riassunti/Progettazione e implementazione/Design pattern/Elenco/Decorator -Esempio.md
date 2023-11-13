```java
public interface Pizza { 
	String toString(); 
}  
public class BaseNormale implements Pizza {     
	public String toString() { return "Io sono una pizza con: base normale";} 
}  
public class BaseIntegrale implements Pizza { 
	public String toString() { return "Io sono una pizza con: base integrale";} 
}  
public abstract class IngredienteDecorator implements Pizza {
	private Pizza base;      
	public IngredienteDecorator(Pizza base) { this.base = base; }      
	public String toString() { return base.toString();} 
}  
public class IngredienteSalame extends IngredienteDecorator {
	public IngredienteSalame(Pizza base) { super(base); }      
	@Override     
	public String toString() { return super.toString() + ", salame"; } 
}  
```

```java
public class Client {     
	public static void Main() { // Voglio una pizza con salame, peperoni e base integrale         
	Pizza salamePeperoni = new IngredientePeperoni( 
		new IngredienteSalame( new BaseIntegrale()  ) ); 
	} 
}
```

```java
public abstract class IngredienteDecorator implements Pizza {     
	private Pizza base;      
	public IngredienteDecorator(Pizza base) { this.base = base; }      
	public String toString() { return base.toString() + nomeIngrediente();}      
	protected String nomeIngrediente() { return ""; } 
}  
public class IngredienteSalame extends IngredienteDecorator { 
	public IngredienteSalame(Pizza base) {super(base);}      
	@Override     
	public String nomeIngrediente() { return ", salame"; } 
}  
public class IngredientePeperoni extends IngredienteDecorator {     
	public IngredientePeperoni(Pizza base) {super(base);}      
	@Override     
	public String nomeIngrediente() { return ", peperoni"; } 
}
```