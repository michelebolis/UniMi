Libreria che usa pesantemente la reflection

```java
when(oggettoMockato.metodo(args)).then_(value);
```

- args: possono essere valori, matchers...
- then_: thenReturn, thenThrows, thenAnswer, thenCallRealMethod

Quando i metodi ritornano void:
```java
do_(values).when(oggettoMockato.metodo(args)).then_(value);
```

Per verificare l'occorrenza di una chiamata con certi parametri 
```java
verify(mockedClass, howmany).method(args)
```
- howmany: times(n), never, atLeast(n), atMost(n)

Per verificare l'ordine delle occorrenze delle chiamate
```java
InOrder inO = inOrder(mock1, mock2, ...)
inO.verify(...)...
```

Per catturare un parametro su cui fare asserzioni
```java
ArgumentCaptor<Person> arg = ArgumentCaptor.forClass(Person.class); verify(mock).doSomething(arg.capture()); 
assertEquals("John", arg.getValue().getName());
```