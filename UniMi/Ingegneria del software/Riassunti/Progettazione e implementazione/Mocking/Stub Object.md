Altre volte risulta difficile testare il SUT perché il suo comportamento dipende dai cosiddetti _input indiretti_: valori restituiti da altri componenti software (DOC) con i quali interagisce. 
Gli **input indiretti** possono essere valori di ritorno dei metodi del DOC, parametri aggiornati, errori o eccezioni sollevate dal DOC.

Test Double con questo scopo prendono il nome di **stub object**: `sostituiscono un componente reale, da cui dipende il SUT, e forniscono risposte` (input) “preconfezionate” alle sole chiamate fatte durante il testing. 
Vantaggio: consente al test di forzare la realizzazione di determinati scenari particolari o di interesse specifico.

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

[[Stub Object - Mockito]]