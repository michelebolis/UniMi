Algoritmo di Linearizzazione usato per evitare classi doppie
Estensione valutata da destra verso sinistra

```scala
class C1 { def m = List("C1") } 
trait T1 extends C1 { override def m = { "T1" :: super.m } } 
trait T2 extends C1 { override def m = { "T2" :: super.m } } 
trait T3 extends C1 { override def m = { "T3" :: super.m } } 
class C2A extends T2 { override def m = { "C2A" :: super.m } } 
class C2 extends C2A with T1 with T2 with T3 { override def m = { "C2" :: super.m } } 

def linearization(obj: C1, name: String) = { 
	val lin = obj.m ::: List("ScalaObject", "AnyRef", "Any") 
	println(name + ": " + lin) 
}
```

```cmd
linearization(new C2,"C2 ")
C2 : List(C2,T3,T1,C2A,T2,C1,ScalaObject,AnyRef,Any)
```

| N   | Linearization                           | Description                                  |
| --- | --------------------------------------- | -------------------------------------------- |
| 1   | C2                                      | add the type of the instance                 |
| 2   | C2, T3, C1                              | Add the linearization for T3                 |
| 3   | C2, T3, C1, T2, C1                      | Add the linearization for T2                 |
| 4   | C2, T3, C1, T2, C1, T1, C1              | Add the linearization for T1                 |
| 5   | C2, T3, C1, T2, C1, T1, C1, C2A, T2, C1 | Add the linearization for C2A                |
| 6   | C2, T3, T2, T1, C2A, T2, C1             | Remove duplicates of C1; all but the last C1 |
| 7   | C2, T3, T1, C2A, T2, C1                 | Remove duplicates of T2; all but the last T2 |
| 8   | C2, T3, T1, C2A, T2, C1, ...      |           Finish                                   |


