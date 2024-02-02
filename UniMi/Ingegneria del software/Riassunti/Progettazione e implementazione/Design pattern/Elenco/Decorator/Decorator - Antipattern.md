Immaginiamo di voler modellare con degli oggetti una grande varietà di pizze differenti sia per la base (_es. normale, integrale, senza glutine…_) che per gli ingredienti che vi si trovano sopra. Per ogni diversa varietà di pizza vorremmo ottenere un oggetto aderente a un’interfaccia comune `Pizza` il cui metodo `toString()` elenchi la base e gli ingredienti che la compongono.

- `Gerarchia di classi`

Un primo approccio _statico_ a questo problema consiste nel `creare una gerarchia di classi che contenga una classe per ogni possibile combinazione` di base e ingredienti, che d’ora in avanti chiameremo “**decorazioni**”.

```java
public interface Pizza {}  
public class BaseNormale implements Pizza {     
	public String toString() { return "Sono una pizza con: base normale";} 
} 
public class BaseIntegrale implements Pizza {     
	public String toString() { return "Sono una pizza con: base integrale";} 
}  
```

Problemi: 
- esplosione combinatoria dovuta all’accoppiamento di ogni possibile base e insieme di decorazioni
- estrema difficoltà che comporterebbe una futura aggiunta di decorazioni.

Alternativa:
- `God class`
L’ideale sarebbe invece poter **aggiungere funzionalità e caratteristiche dinamicamente**, restringendo la gerarchia ad un’unica classe le cui istanze possano essere “decorate” su richiesta al momento dell’esecuzione.  
La soluzione più semplice a questo nuovo problema parrebbe quella che viene definita una GOD CLASS (o _fat class_), ovvero `un’unica classe in cui tramite attributi booleani e switch vengono attivate o disattivate diverse decorazioni.`

```java
public class GodPizza {      
	boolean baseNormale = false;     
	boolean baseIntegrale = false;     
	...
	public void setBaseNormale(boolean status) { baseNormale = status; }     
	public void setBaseIntegrale(boolean status) { baseIntegrale = status; }     
	...      
	public String toString() {         
		StringBuilder sb = new StringBuilder("Sono una pizza con: ");         
		if (baseNormale) sb.append("base normale, ");         
		if (baseIntegrale) sb.append("base integrale, ");         
		...        
		return sb.toString();     
	} 
}
```

Problemi: 
- chiara violazione dell’Open-Close Principle, in quanto per aggiungere un decoratore è necessario modificare la God Class
- diventa molto velocemente gigantesca, zeppa di funzionalità tra loro molto diverse (_scarsa separazione delle responsabilità_) e decisamente infernale da leggere, gestire e debuggare in caso di errori.