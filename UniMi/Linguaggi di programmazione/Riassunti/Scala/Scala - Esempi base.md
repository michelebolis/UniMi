
es Upper cases
```scala
class Upper { 
	def upper(strings: String*): Seq[String] = {
	 strings.map((s:String) => s.toUpperCase()) 
	} 
} 
val up = new Upper 
Console.println(up.upper("A", "First", "Scala", "Program"))
```

```cmd
scala upper.scala
OPPURE
scalac upper.scala //ATT SOLO SE TUTTO il codice è una classe o object
OPPURE
scala //entro nell interprete
:load upper.scala
```

Semplificando
```scala
object Upper { 
	def upper(strings: String*) = strings.map(_.toUpperCase()) 
} 
println(Upper.upper("A", "First", "Scala", "Program"))
```

Semplificando
```scala
object Upper { 
	def main(args: Array[String]) = {
		args.map(_.toUpperCase()).foreach(printf("%s ",_)) 
		println("")
	} 
}
```

[[Scala - Es Known Functions]]