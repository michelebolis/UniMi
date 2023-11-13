```java
@Test 
public void testConSpy() {
     MyClass spy = spy(new MyClass());

     MyList<int> SUT = new MyList<int>();

     res = SUT.somma(spy);
     
     assertThat(res).isEqualTo(14); 
     InOrder io = inOrder(spy); 
     io.verify(spy).getValue(0); 
     io.verify(spy, times(2)).getValue(1);
} 
```