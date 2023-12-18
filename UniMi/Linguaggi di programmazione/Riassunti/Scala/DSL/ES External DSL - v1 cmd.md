```cmd
import scala.util.parsing.combinator._ 
import payroll.pcdsl._
val p = new PayrollParserCombinatorsV1
p.empl // res0: p.Parser[String] = Parser (~>)
p.weeksDays // res2: p.Parser[String] = Parser (|)
p.paycheck // res3: p.Parser[p.~[p.~[String,p.~[String,String]],List[String]]] = Parser (~)

p.parseAll(p.weeksDays, "weeks") 
	// res4: p.ParseResult[String] = [1.6] parsed: weeks
val input = """paycheck for employee "Buck Trends" | 
			is salary for 2 weeks minus deductions for {}""" 
p.parseAll(p.paycheck, input)
	// res5: p.ParseResult[p.~[p.~[String,p.~[String,String]],List[String]]] = [2.46] parsed: (("Buck Trends"~(2~weeks))~List())

val input = """paycheck for employe "Buck Trends" | 
			is salary for 2 weeks minus deductions for {}"""
p.parseAll(p.paycheck, input)
	// res6: p.ParseResult[p.~[p.~[String,p.~[String,String]],List[String]]] = [1.14] failure: 'employee' expected but ' ' found paycheck for employe "Buck Trends"
```