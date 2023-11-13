```java
@Test public void testConStub() { 
	MyClass stub = mock(MyClass.class); 
	when(stub.getValue(0)).thenReturn(4); 
	when(stub.getValue(1)).thenReturn(7, 3); 
	MyList<int> SUT = new MyList<int>(); 
	SUT.add(stub.getValue(0)); // deve ritornare 4 
	SUT.add(stub.getValue(1)); // deve ritornare 7 
	SUT.add(stub.getValue(1)); // deve ritornare 3 
	res = SUT.somma(); 
	assertThat(res).isEqualTo(14); 
}
```