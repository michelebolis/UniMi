Approccio al testing: 
- metodo restituisce un valore: assert sui risultati di un metodo
- metodo che modifica lo stato: uso il method e poi uso un getter 
- metodo che modifica lo stato MA usando altri metodi di altre classi (dependent component):
	- il mio oggetto chiede dell'input (indirettamente testo anche la correttezza dei componenti che utilizza; se il risultato è sbagliato non sapro da dove provenga l errore)
	- il mio oggetto non attua cambiamento al suo stato, ma a quello di un altro oggetto, quindi devo usare un test che verifichi lo stato del dependent component

Il problema è che magari il componente esterno magari non è ancora stato implementato 
Vogliamo sostituire tutto cio che non è il componente sotto test, con qualcosa il piu semplice, veloce e fittizzio possibile

Dummy objects
Oggetti che sono passati in giro ma mai veramente usati
- non posso passare null
- potrei avere solo una interfaccia e non una classe
- potrei avere solo costruttori complessi

```java
@Test
public void testDummy(){
	MyClass dummy = ??;
	List<MyClass> SUT = new ArrayList<MyClass>();
	SUT.add(dummy);
	assertThat(SUT.size()).isEqualTo(1);
}
```

Stub Object
- oggetti che forniscono risposte preconfezionate alle sole chiamate fatte durante il testing

```java
@Test
public void testStub(){
	MyClass stub = ??;
	List<int> SUT = new ArrayList<int>();
	
	SUT.add(stub.getValue(0)); //voglio 4
	SUT.add(stub.getValue(1)); //voglio 7
	SUT.add(stub.getValue(1)); //voglio 3
	res = SUT.somma();
	assertThat(res).isEqualTo(14);
}
```

Mock objects
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

- Spy objects
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

- Fake objects
...


Mockito
Libreria che usa pesantemente la reflection

es
MyClass dummy = mock(MyClass.class)

MyClass stub = mock(MyClass.class)
when(stub.getValue(0)).thenReturn(4)
when(stub.getValue(1)).thenReturn(7, 3)

InOrder io = inOrder(mock)
io.verify(mock).getValue(0);
io.verify(mock, times(2)).getValue(1)


MyClass spy = spy(new MyClass())

...