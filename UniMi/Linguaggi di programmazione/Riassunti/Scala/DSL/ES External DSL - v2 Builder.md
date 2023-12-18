```scala
import payroll._ 
import payroll.Type2Money._ 
import payroll.pcdsl._ 
object PayRollBuilder { 
	def main(args: Array[String]) = { 
		val buck = Employee(Name("Buck", "Trends"), Money(80000)) 
		val jane = Employee(Name("Jane", "Doe"), Money(90000)) 
		val employees = Map(buck.name -> buck, jane.name -> jane) 
		val p = new PayrollParserCombinators(employees) 
		args.foreach { filename => 
			val src = scala.io.Source.fromFile(filename) 
			val lines = src.mkString 
			p.parseAll(p.paycheck, lines) match { 
				case p.Success(Pair(employee, paycheck),_) => 
					print(format("%s %s: %s\n", employee.name.first, employee.name.last, paycheck)) 
				case x => print(x.toString) 
			} 
			src.close() 
		} 
	} 
}
```

test1: paycheck for employee "Jane Doe" is salary for 2 weeks minus deductions for {}
test2: paycheck for employee "Buck Trends" is salary for 2 weeks minus deductions for { 
	federal income tax is 25. percent of gross, 
	state income tax is 5. percent of gross, 
	insurance premiums are 500. in gross currency, 
	retirement fund contributions are 10. percent of gross 
}
test3: paycheck for employee "John Doe" is salary for 2 weeks minus deductions for {}

```cmd
scala PayRollBuilder test1.pr test2.pr test3.pr
 // Jane Doe: Paycheck($3461.54,$3461.54,$0.00) 
 // Buck Trends: Paycheck($3076.92,$1346.15,$1730.77)
 // payroll.pcdsl.UnknownEmployee: Name(John,Doe) at 
	payroll.pcdsl.PayrollParserCombinators$$anonfun$empl$4.apply(payroll-pc.scala:24
```