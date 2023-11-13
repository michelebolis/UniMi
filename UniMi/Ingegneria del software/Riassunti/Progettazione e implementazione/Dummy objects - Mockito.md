```java
@Test public void testDummy() { 
	MyClass dummy = mock(MyClass.class); 
	List<MyClass> SUT = new ArrayList<MyClass>(); 
	SUT.add(dummy); 
	assertThat(SUT.size()).isEqualTo(1); 
}
```