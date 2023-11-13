Oggetti che instrumentano e controllano le chiamate

```java
@Test
public void testConMock(){
	MyClass mock = ??;
	List<int> SUT = new ArrayList<int>();
	res = SUT.somma(mock);
	assertThat(res).isEqualTo(14);
}
```

Testo l interazione della classe: quante volte è stato il chiamato il metodo..., con quali argomenti...
