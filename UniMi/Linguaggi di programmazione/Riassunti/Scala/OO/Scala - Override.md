Sia le classi che i trait possono dichiarare dei membri `abstract`: i campi, i metodi e i **tipi** (`type nomeTipoGenerico`)
I membri astratti DEVONO essere definiti da una classe o trait prima che l'istanza sia creata

`override` è opzionale quando override un membro astratto

[[Linearization Algorithm]]

```scala
import java.io._ 
abstract class BulkReader { 
	type In 
	val source: In 
	def read: String 
} 
class StringBulkReader(val source: String) extends BulkReader { 
	type In = String // faccop override dell'abstract type
	def read = source 
} 
class FileBulkReader(val source: File) extends BulkReader { 
	type In = File 
	def read = { 
		val in = new BufferedInputStream(new FileInputStream(source)) 
		val numBytes = in.available() 
		val bytes = new Array[Byte](numBytes) 
		in.read(bytes, 0, numBytes) 
		new String(bytes) 
	} 
} 
println( new StringBulkReader("Hello Scala!").read ) 
println( new FileBulkReader(new File("BulkReader.scala")).read )
```

