ES

```scala
val p = new PayrollParserCombinatorsV1 
p.parseAll(p.paycheck, input) match { 
	case p.Success(r,_) => ... 
	case x => ... 
}
```

`parseAll` è definita in una classe che riceve un parser e un input come stringa da parsare
SE il parsing ha successo, il risultato è un'istanza di `p.Success(r, _)` un caso dichiarato nel trait Parsers con
- `r` il risultato del parsing di tipo T
- \_ input rimanente da parsare 
`p.` indica che è un tipo path-dependent e permette di distinguire il risultato da due parsers
SE il parsing fallisce, l'istanza ritornata è o `p.Failure` o `p.Error`, entrambe derivanti da `p.NoSuccess`