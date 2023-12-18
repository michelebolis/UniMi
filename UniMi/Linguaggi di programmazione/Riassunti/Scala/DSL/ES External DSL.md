[[ES External DSL - Grammatica]]
[[ES External DSL - v1]]

Dara una semantica al DSL
Quando parsiamo dobbiamo cercare l employee in base al nome, prendere il suo salario per il periodo specificato e calcolarne la deduzione
Quando il parsing finisce, dobbiamo restituire una coppia Employee, Paycheck

[[ES External DSL - v2]]

Considerazioni
Il parser usa una mappa di Name per semplicità
`currentEmployee` contiene l'Employee che si sta parsando e `grossAmount` il suo salario per il periodo

`p^^f` è un combinator che applica `f` al risultato di `p` quando ha successo 

Questo parser è un evoluzione che tiene in considerazione il risultato finale
```scala
def paycheck = empl ~ gross ~ deduct ^^ {
	case e ~ g ~ d => (e, Paycheck(g, g-d, d))} 
```