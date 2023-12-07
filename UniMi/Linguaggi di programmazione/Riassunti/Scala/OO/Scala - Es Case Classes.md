```scala
object TermTest extends Application { 
	def printTerm(term: Term) { 
		term match { 
			case Var(n) => print(n) 
			case Fun(x, b) => print("λ" + x + "."); 
				printTerm(b) 
			case App(f, v) => Console.print("("); 
				printTerm(f) print(" "); printTerm(v); print(")") 
		} 
	} 
	def isIdentityFun(term: Term): Boolean = 
		term match { 
			case Fun(x, Var(y)) if x == y => true 
			case _ => false 
		} 
	
	val id = Fun("x", Var("x")) 
	val t = Fun("x", Fun("y", App(Var("x"), Var("y")))) 
	printTerm(t); println; println(isIdentityFun(t)) 
	printTerm(id); println; println(isIdentityFun(id)) 
}
```

```cmd
λx.λy.(x y) 
false 
λx.x true
```