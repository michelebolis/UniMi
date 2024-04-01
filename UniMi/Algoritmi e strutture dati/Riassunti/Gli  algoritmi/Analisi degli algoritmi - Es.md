Es moltiplicazione: vari approcci
In colonna 19 x 114 = 2.166
Quante operazioni facciamo?
\#prodotti a 1 cifra= lunghezza di a * lunghezza di b
\#somme di numeri= lunghezza di b
Numero di cifre = log

Prodotto come serie di somme $a*b= a+a+a+…+a$ //b volte
ALGORITMO moltiplicazione(intero a, intero b) --> intero
```
1 prod <- 0 //assegnamento, freccia per indicare direzione
2 WHILE  b>0 DO
	3 prod <- prod + a
	4 b <- b-1
5 RETURN prod
```
![[Pasted image 20240329091745.png]]

Correttezza: cerchiamo di vedere come evolvono, la variabile a non viene mai modificata mentre b e prod si.
Caso base: $b_0$ valore iniziale di $b_0=b$, $prod_0=0$ --> vero
Passo caso $i$: i-1 --> i, $b_i=b_{i-1} -1$= 
per ipotesi di induzione $b-(i-1)-1=b-i+1-1=b-i$, 
$prod_i=prod_{i-1} +a$ =
per ipotesi di induzione $a*(i-1)+a=a*i-a+a=a*i$
$b_i =0$, SE i=b all'iterazione b $prod_b=a*b$

Efficienza: quanto tempo impiega? Difficile da stabilire
Quanto cresce il tempo all'aumentare dei numeri?
Supponiamo che ogni riga di codice abbia tempo unitario
SE $b=0$ eseguo 1, 2 e 5
SE $b>0$ eseguo 1 e 5 1 volta + 3-4 le eseguo b volte + 2 la eseguo b+1 --> 2+2b+b+1=3b+3
$T(a, b)= 3b+3$ //tempo indipendente da a

Quanta memoria utilizziamo? 3 variabili interi di cui 2 parametri

Moltiplicazione alla russa: moltiplicando a * moltiplicatore b
Divido il moltiplicando per 2 e il moltiplicando lo divido per 2 finché b non è a 0 o 1
Copio i moltiplicandi quando il moltiplicatore è dispari sommando tutti i moltiplicandi trovati.

$$ab=\begin{cases} 2*a*(b/2) SE \text{ b pari} \\ 2*a*(b/2)+a \text{ SE b dispari con } b\neq 1 \\ a \text{ SE b=1} \end{cases}$$

```
ALGORITMO moltiplicazione (intero a, intero b)-> intero
1 prod<-0
2 WHILE b>0 DO
3 IF b dispari THEN
4 prod <- prod +a
5 b <- b/2
6 a <- a*2
7 RETURN prod
```

![[Pasted image 20240329092334.png]]

$a_i*b_i + prod_i= a*b$
CASO BASE $i=0$ $a_0=a, b_0=b, prod_0=0$
$a*b+0=a*b$

INDUZIONE $i-1 -> i$
1. Caso pari $b_{i-1}$

$b_i=\frac{b_{i-1}}{2}, a_i=a_{i-1}*2, prod_i=prod_{i-1}$
$a_{i-1}*2 + \frac{b_{i-1}}{2} + prod_{i-1} = a_{i-1} * b_{i-1} + prod_{i-1}$ = PER IPOTESI INDUTTIVA $a*b$

1. Caso dispari $b-1$
$b_i=[\frac{b_{i-1}}{2}]=\frac{b_{i-1}-1}{2}, a_i=2*a_{i-1}, prod_i=prod_{i-1} -a_{i-1}$
$2*a_{i-1} * \frac{b_{i-1}-1}{2} + prod_{i-1} - a_{i-1} = a_{i-1} * b_{i-1} -a_{i-1} + prod_{i-1} + a_{i-1}$ = PER IPOTESI INDUTTIVA $a*b$

Supponendo $u$ iterazioni
Linea 1 e 7 eseguite 1 volta + 2 $u+1$ volte + 3,5,6 $u$ volte + 4 da 0 volte (se b potenza di 2) a $u$ volte quindi <= $u$ volte  = <= $5u+3$

b=0 --> u=0, b=1 --> u=0, b=2 --> u=2, b=3 --> u=2, b=4 --> u=3 …
$u= \lfloor log_2 b \rfloor + 1$ 
$T(a, b)= 5(\lfloor log_2 b \rfloor +1) +3 = 5 \lfloor log_2 b \rfloor + 8$


es potenza
```
ALGORITMO potenza(intero x, intero y) --> intero
1 power <-1
2 IF y!=0 THEN
3 power <- potenza(x, y/2) //divisione intera
4 power <- power * power
5 IF y dispari THEN
6 power <- power * x
7 RETURN power
```

Questo è lo stesso algoritmo
SE $y=0$ eseguo 1,2,7: 3
SE $y>0$ eseguo 1,2,3,4,5,7 (6): $<=7 + T(x, \frac{y}{2})$

$T(x, y) <= 3$ SE $y=0$
	$7 + T(x, \lfloor \frac{y}{2} \rfloor)$ altrimenti

$T(x, y) <= 7 log_2 y +10$
In realtà le costanti del tempo non sono importanti ma l'analisi si focalizzi su quanto velocemente aumenta il tempo, quindi il $log_2 y$