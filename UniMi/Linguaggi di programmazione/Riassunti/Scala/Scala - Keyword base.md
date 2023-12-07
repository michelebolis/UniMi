- `class{...}` definisce una classe
- `object{...}` definisce una classe con una sola istanza (singleton)
- Numero variabile di argomenti:  `*` (è utilizzato come in Java `...`) 
- Definizione funzione: 
`def nomeF(nomeArg: Arg): tipoRitornato = {FBody}`
- Definizione funzione generica: 
`def nomeF[T1, T2](nomeArg: T1): T2 = {FBody}`
- `_` wildcard
- `val` variabile IMMUTABILE
- `var` variabile MUTABILE
- Pattern matching:
variabile match {
		Case ... =>
}
- Pattern matching su lista: `h::tl`
- Concatenazione liste: `:::` (NO `++`)