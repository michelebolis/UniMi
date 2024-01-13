Mockito è una libreria che usa pesantemente la reflection

Una classe di test deve avere l'annotazione `@Test`

Il test in se è solitamente:
- Controllo di un valore restituito
```java
assertThat(SUT.get()).isEqualTo(constante)
assertThat(SUT.isCondizione()).isTrue()
```
- Controllo su un `Iterable`
```java
assertThat(SUT.iterator()).containsExactly(elem1, elem2, elem3);
assertThat(SUT.iterator()).containsExactlyInAnyOrder(elem1, elem2, elem3);
assertThat(SUT.iterator()).hasSize(3);
```
- Controllo sulle eccezioni
```java
assertThatThrownBy(() -> SUT.method()). isInstanceOf(IllegalArgumentException.class).hasMessage("Errore");
```
- Verificare l'occorrenza di una chiamata con certi parametri, per resettare il conteggio `clearInvocations(mockedObject)`
```java
verify(mockedObject, times(1)).method(args)
verify(mockedObject, never).method(args)
verify(mockedObject, atLeast(2)).method(args)
verify(mockedObject, atMost(2)).method(args)
```
- Per verificare l'ordine delle occorrenze delle chiamate
```java
InOrder inO = inOrder(mock1, mock2, ...)
inO.verify(...)...
```
- Per catturare un parametro su cui fare asserzioni
```java
ArgumentCaptor<A> arg = ArgumentCaptor.forClass(A.class); verify(mockedObject).doSomething(arg.capture()); 
assertEquals("John", arg.getValue().getName());
```

Problema: dependent object 
1. Dependent object nei parametri del costruttore
Mockando l'oggetto ogni suo metodo non fa niente e non ha stato MA potrei avere la necessita che alcuni suoi metodi facciano qualcosa o restituiscano qualcosa
```java
A mockedObject = mock(A.class)
```
- Il metodo deve restituire sempre un valore
```java
when(mockedObject.method()).thenReturn(value);
```
- Il metodo deve restituire un iteratore (ATT se ritornassi semplicemente l iteratore, lo potrei usare solo una volta)
```java
when(mockedObject.iterator()).thenAnswer(
	invocation -> List.of(...).iterator()
);
```
- Il metodo deve agire come quello della classe se non fosse mockato
```java
when(mockedObject.method()).thenCallRealMethod();
```
- Il metodo ritorna void
```java
doAnswer(invocation -> {
	String s = (String) invocation.getArguments()[0];
	when(mockedObject.get()).thenReturn(nome);
	return null;
}).when(mockedObject).set(anyString());
```

2. Dependent object non nei parametri del costruttore costruttore
Si utilizza l'`Injection` MA prima bisogna settare la classe di Test
```java
@ExtendWith(MockitoExtension.class)
class ATest {
    @Mock
    B mockedObject;
    @InjectMocks
    A SUT;
}
```
In questo caso A ha come stato B che viene mockato e iniettato. In qualsiasi test successivo sarà possibile dichiarare `when(...)`, `do...` e cosi via

Ottimizzazioni possibili
- Testing parametrico
```java
@ParameterizedTest
@CsvSource({
        "1,a",
        "2,b"
})
void parametricTest(int n, String s) {
    assertThat(c.convert(n)).isEqualTo(s);
}
```
- Metodo da eseguire prima di ciascun test
```java
@BeforeEach
void setup() {
    this.SUT = new SUT()
}
```

Test tipici nel MV
- `Presenter`
	- Verificare che se l'input nel metodo `action` è sbagliato, venga richiamato `showError("...")` nella vista associata
	- Verificare che se l'input nel metodo `action` è corretto, venga richiamato `showSuccess()` nella vista associata
	- Verificare che dopo un `update`,  venga aggiornata la vista associata
- `Model`
	- Verificare che dopo l'utilizzo del setter, ritorno lo stato appena settato con un getter
	- Verificare che dopo l'utilizzo di un setter errato, venga sollevata l'eccezione desiderata
	- Verificare che dopo l'utilizzo del setter, venga fatto l'update per tutti gli observer (che andranno quindi mockati e aggiunti con `SUT.addObserver(obs)`)