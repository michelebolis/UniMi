Formule booleane in forma normale congiuntiva
- $V$ insieme finito di variabili
- Letterale è una variabile o una variabile negata
- Clausula è una disgiunzione di letterali es $x \vee y$
- Formula è una congiunzione di clausole es $\Phi(x, y, z)= (x \vee y) \wedge (x \vee z)$
- Assegnamento $f: V --> \{0, 1\}$
	$\Phi(f)$ è il valore della formula f assegnando a ogni variabile il valore di f(x)

Problema di soddisfacibilità / SODD
Istanza: Formula booleana $\Phi$ in forma normale congiuntiva con insieme di variabili $V$
Questione: esiste un assegnamento alle variabili in $V$ che rende vera $\Phi$, cioè t.c. $\Phi(f)=1$

$Φ(x_1, x_2, …, x_n)$ formula con $n$ variabili
Per decidere SE $\Phi$ è soddisfacibile, proviamo tutti i possibili assegnamenti di valori alle variabili, che sono $2^n$
$SODD \in EXPTIME$

In realta $SODD \in NP$