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