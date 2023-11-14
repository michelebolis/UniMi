Ad una variabile che indica un riferimento a un oggetto possiamo assegnare un valore null
Problema: quando proviamo a deferenziale la variabile e non puntando a nulla, riceviamo un errore

Null viene utilizzato per indicare errore, stato temporaneamente inconsistente, valore assente.
Perciò un codice chiaro NON dovrebbe far uso di null o almeno limitarlo

come implementare attributi diversi da null: 
assert attributo!=null;


modalita sviluppo: faccio un if --> segnalo io l errore dell utilizzatore, programmazione difensiva

```java
public Card(Rank rank, Suit suit) { 
	if (rank == null || suit == null) 
		throw new IllegalArgumentException(); 
	this.rank = rank; this.suit = suit; 
}
```

modalita produzione: assert o notazione --> assumo l utilizzo corretto, programmazione con contratto

```java
final @NotNull private Rank rank; 
final @NotNull private Suit suit; 
public Card(@NotNull Rank rank, @NotNull Suit suit) { 
	this.rank = rank; 
	this.suit = suit; 
}
```
