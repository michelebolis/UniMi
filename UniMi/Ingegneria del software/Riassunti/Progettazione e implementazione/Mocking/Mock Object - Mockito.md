```java
@Test 
public void testConMock() {
     MyClass mock = mock(MyClass.class);
     
     when(mock.getValue(0)).thenReturn(4); 
     when(mock.getValue(1)).thenReturn(7,3);

     MyList<int> SUT = new MyList<int>();

     res = SUT.somma(mock);
     
     assertThat(res).isEqualTo(14); 
     InOrder io = inOrder(mock); 
     io.verify(mock).getValue(0); 
     io.verify(mock, times(2)).getValue(1);
} 
```
