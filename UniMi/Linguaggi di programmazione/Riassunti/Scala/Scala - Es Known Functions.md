```scala
def map[A,B](f: A=>B, list: List[A]): List[B] = 
	list match { 
		case Nil => Nil
		case hd::tl => f(hd)::map[A,B](f,tl) 
	} 
def reduce[T](f:(T,T)=>T, list:List[T]): T = { 
	def reduce2(acc:T, list:List[T]): T = 
		list match { 
			case Nil => acc 
			case hd::tl => reduce2(f(acc,hd), tl) 
		} 
	reduce2(list.head, list.tail) 
} 
def exists[T](p: T=>Boolean, list:List[T]): Boolean = { 
	var exists = false; 
	for (elem <- list if p(elem)) exists = true; exists 
} 
def forall[T](p: T=>Boolean, list:List[T]): Boolean = 
	reduce( (X:Boolean,Y:Boolean)=>X&&Y, map(p, list) ) 
def quicksort[T](lt: (T,T) => Boolean, list:List[T]): List[T] = { 
	list match { 
		case Nil => Nil 
		case pivot::tl => 
			val (p1, p2) = tl.partition( (X:T) => lt(X, pivot) ) 
			quicksort(lt, p1) ::: (pivot::Nil) ::: quicksort(lt, p2) 
	} 
}
```