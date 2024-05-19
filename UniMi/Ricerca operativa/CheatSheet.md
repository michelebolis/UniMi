1. PL/PLI (Gusek)

| Componente                | Codice dichiarazione                          | Codice assegnamento         |
| ------------------------- | --------------------------------------------- | --------------------------- |
| Parametro unico           | `param n;`                                    | `param := 10;`              |
| Insieme indice numerico   | `set R := 1..n;`                              | \                           |
| Insieme indici testuali   | `set C;`                                      | `set C := Cane Gatto;`      |
| Vettore                   | `param q{C};`                                 | `param q := Cane 1 Gatto 2` |
| Variabile                 | `var X >= lowerBound,`<br>`<= upperBound`<br> | \                           |
| Vincolo                   | `subject to Vincolo : ...`                    |                             |
| Obiettivo minimizzazione  | `minimize z : ...`                            |                             |
| Obiettivo massimizzazione | `maximize z : ...`                            |                             |

Altri componenti
- Matrice
```ampl
param M{R, R};
param M : 1   2 :=
1        0.1 0.2
2        0.2 0.1
;
```

Situazioni ricorrenti
- Massimizzare un minimo

Dichiaro una variabile di appoggio in cui calcolo il minimo `y` attraverso un vincolo 
`subject to Vincolo : y <= ...`
Massimizzo nella funzione obiettivo y

- Serie di lower e upper bound

Creo due vettori/matrici, uno che conterrà i lower bound e uno gli upper bound
Creo due vincoli per far rispettare i due bound
SE bound in %, `subject to Vincolo {i in N} : x[i] <= lowerBound[i]*...`
SE bound quantitativi, `subject to Vincolo {i in N} : x[i] <= lowerBound[i]`

- Solo una parte di un insieme è utilizzata per un parametro

Dato l'insieme `set M;`, dichiaro un altro insieme `set M2 within M;` che utilizzerò per l altro parametro `param q{M2};`

- Vincolo solo su una parte di un insieme

```ampl
set N := 1..10;
subject to Vincolo {i in N : i>5} : ...
```

- Variabili intere o binarie

```ampl
var x{N} integer >= 0;
var y{N} binary default 0; # Usate spesso in produttorie per ignorare un fattore
```

- Quando utilizzo variabili binarie su una matrice{N, M} solitamente c è un vincolo che la somma o sulle righe o sulle colonne sia =1  
- Variabili binarie si utilizzano per esprime ogni possibilita di per es coppie
- Vettore di coppie in un insieme 

```ampl
set P := 1..n;
set V within (P cross P);
subject to Vincolo{i in P} : sum{(i, j) in V} ... ;
set V := 
1 2
2 2
;
```

- Vettore di variabili binarie con chiave un vettore

```
param calendario{giornate, partite, squadre} binary default 0;
param calendario :=
[1,1,1] 1
;
```

- Vettore di vettori con lunghezza non fissa

```ampl
set VoliSequenza{Sequenze} within Voli;
param : Sequenze : costi :=
  A01     1200
;
set VoliSequenza[A01] := 1  2  3  4  5;
```

- Vincolo `|a-b| < k`

```ampl
subject to Mod1 {f1 in Frequenze, f2 in Frequenze : 
 (val[f1] > val[f2]) and (val[f1] - val[f2] < k)} : ...
```

- Analisi post-ottimale

`Tools` -> `Generate LP Sensitivity Analysis` permette di generare un ulteriore file
Sulla colonna `Obj coef` notiamo il coefficiente della funzione obiettivo 
Sulla colonna `Marginal` il valore delle variabili fuori base (negative/positive SE maximize/minimize), quindi quanto dovrebbe aumentare/diminuire il coefficiente per far entrare in base la variabile
Per quanto riguarda invece le variabili in base, il range di valori del coefficiente per cui la variabile resta in base è presente nella colonna `Obj coef range`

2. PLN (AMPL)

```ampl
model nomeFile.mod;
data nomeFile.txt;
option solver nomeSolver;# Setto il risolutore
solve;
reset;
```

OSS anche con problemi semplici, aspettarsi errori a causa dei vincoli
Per inizializzare la variabile, cioe da dove parte il risolutore, nella variabile scrivere `:= ...` es `:= 1` perché di default magari parte da 0 o una quantita che si avvicina all upper/lower bound

Solver:
- snopt: non lineare
- minos: lineare
- lindo: non lineare intero

Funzioni non lineare di AMPL
- `x mod y` modulo 
	- cercare di avere sempre numeri positivi es `i-1 mod 3` -> `i+2 mod 3`
	- sui parametri su cui uso il mod, cercare di avere indici da 0 a n-1 piuttosto che da 1 a n
- `sqrt(x)` radice quadrata