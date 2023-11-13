Oggetti che instrumentano e controllano le chiamate di oggetti reali

```java
@Test
public void testConSpy(){
	MyClass spy = ??; // DEVE gia esistere una classe reale MyClass
	List<int> SUT = new ArrayList<int>();
	res = SUT.somma(spy);
	assertThat(res).isEqualTo(14);
}
```
