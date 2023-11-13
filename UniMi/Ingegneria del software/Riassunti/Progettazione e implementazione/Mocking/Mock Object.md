Oggetti che instrumentano e controllano le chiamate

Il comportamento del SUT può includere azioni che non possono essere osservate attraverso la sua API pubblica, ma che sono osservate o sperimentate da altri sistemi o componenti dell’applicazione. Tali attività ricadono sotto il nome di **output indiretti** del SUT. 
Gli output indiretti possono includere chiamate a metodi di un altro componente, record inseriti in un database, record scritti su un file _etc_.

Testare il comportamento del SUT può voler dire anche verificare che gli output indiretti siano quelli corretti e a tale scopo servono punti di osservazione appropriati. Un **punto di osservazione** è un modo con cui il test può ispezionare lo stato post-exercise del SUT. 
I punti di osservazione utili a verificare gli output indiretti sono costituiti da Test Double che prendono il nome di **mock object**. Questi intercettano gli output indiretti del SUT nella fase di exercise e permettono di confrontarli con gli output attesi in un momento successivo (_i.e._ la fase di verifying).

Un mock object è dunque utilizzato per instrumentare e controllare le chiamate fatte dal SUT. 
In genere, l’oggetto Mock include anche la funzionalità di uno Stub; deve infatti essere in grado di restituire valori al SUT, anche se l’enfasi è posta sulla _verifica_ delle chiamate effettuate e non dal loro risultato.

```java
@Test
public void testConMock(){
	MyClass mock = ??;
	List<int> SUT = new ArrayList<int>();
	res = SUT.somma(mock);
	assertThat(res).isEqualTo(14);
}
```

es testo l interazione della classe: quante volte è stato il chiamato il metodo..., con quali argomenti...

[[Mock Object - Mockito]]