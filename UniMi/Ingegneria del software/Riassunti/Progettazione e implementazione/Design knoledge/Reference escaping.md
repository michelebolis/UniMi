Reference escaping: accesso a un attributo privato fuori dalla classe
Situazioni:
- Getter ritorna un riferimento di un attributo privato 

```java
private List<Card> cards; 
public List<Card> getCards() { 
	return this.cards; 
}
```

- Setter assegna ad un attributo privato un riferimento che gli viene passato

```java
private List<Card> cards; 
public setCards(List<Card> cards) { 
	this.cards = cards; 
}
```

- Costruttore assegna ad un attributo segreto un riferimento che gli viene passato

```java
private List<Card> cards; 
public Deck(List<Card> cards) { 
	this.cards = cards; 
}
```