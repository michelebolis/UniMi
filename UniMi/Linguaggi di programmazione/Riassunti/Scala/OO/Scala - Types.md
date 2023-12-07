`Any` è la root della gerarchia seguita da
- `AnyRef` la root della gerarchia delle classi per riferimento (`Object` in Java)
- `AnyVal` la root dei tipi base

Empty values (bottom nella gerarchia)
- `Null` per tutti i tipi per riferimento, instanziabile con `null`
- `Nothing` per tutti i tipi che non possono essere instanziati

es Empty come List\[Nothing] per ogni List\[T]

![[Pasted image 20231207102600.png]]

Tutto è un oggetto e ogni operazione è un metodo
Keyword:
- `abstract` classe astratta
- `extends` per estendere una classe