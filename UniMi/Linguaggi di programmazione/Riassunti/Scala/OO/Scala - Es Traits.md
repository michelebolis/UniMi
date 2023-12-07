```scala
trait T1 { println(" in T1: x = " + x); val x=1; println(" in T1: x = " + x) } 
trait T2 { println(" in T2: y = " + y); val y="T2"; println(" in T2: y = " + y) } 
class Base12 { 
	println(" in Base12: b = " + b); val b="Base12"; println(" in Base12: b = "+b) } 

class C12 extends Base12 with T1 with T2 { 
	println( " in C12: c = "+c); 
	val c="C12"; println(" in C12: c = "+c) 
} 

println( "Creating C12:" ); 
new C12; 
println( "After Creating C12" )
```

```cmd
Creating C12: 
 in Base12: b = null //viene estesa C12 con Base12
 in Base12: b = Base12 
 in T1: x = 0 //viene estesa C12 con il trait T1
 in T1: x = 1 
 in T2: y = null //viene estesa C12 con il trait T2
 in T2: y = T2 
 in C12: c = null //viene eseguito il costruttore di C12
 in C12: c = C12 
After Creating C12
```