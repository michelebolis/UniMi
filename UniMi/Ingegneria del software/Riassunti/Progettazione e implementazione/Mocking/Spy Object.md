Un altro modo per implementare punti di osservazione che controllino e instrumentino le chiamate effettuate dal SUT su determinati DOC sono gli **spy object**. 

A differenza dei mock, questi sono `costruiti a partire da oggetti reali`.  
Successivamente alla fase d’interazione con il SUT (exercise), durante la fase di verifica dei risultati (verify), il test confronta le chiamate effettuate dal SUT sul Test Spy con il comportamento desiderato (expected).

```java
@Test
public void testConSpy(){
	MyClass spy = ??; // DEVE gia esistere una classe reale MyClass
	List<int> SUT = new ArrayList<int>();
	res = SUT.somma(spy);
	assertThat(res).isEqualTo(14);
}
```

[[Spy Object - Mockito]]