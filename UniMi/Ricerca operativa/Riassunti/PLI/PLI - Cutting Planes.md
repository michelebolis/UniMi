Dato un problema di PLI (all'iterazione $k$), consideriamo il suo `rilassamento continuo` e la sua soluzione ottima $x^{*(k)}$
$$P^{(k)} = max\{cx : Ax \leq b, x \in Z^n_+\}$$
$$L^{(k)} = max\{cx : Ax \leq b, x \in R^n_+\}$$
Generiamo un `insieme di disuguaglianze valide/cutting planes` $Qx \leq q$ t.c.
- $Qx \leq q, \forall x \in Z^n_+ : Ax \leq b$ //`non devono escludere nessuna soluzione ammissibile`
- $Qx^{*(k)} > q$ //`devono rendere inammissibile il punto frazionario` $x^{*(k)}$

e otteniamo cosi una formulazione piu stretta
$$P^{(k+1)} = max\{cx : Ax \leq b, Qx \leq q, x \in Z^n_+\}$$

es
![[Pasted image 20240318104509.png|400]]

Gli algoritmi cutting planes `iterativamente risolvono il rilassamento continuo` $L$ di un problema discreto P e `rafforzano la sua formulazione generando ulteriori vincoli` (cutting planes) in modo tale che la soluzione ottima di rilassamento continuo all'iterazione $k$ diventi inammissibile all'iterazione $k+1$
Vantaggi: 
- SE i piani di taglio sono generati in modo efficace, l'`algoritmo di trovare la soluzione ottima discreta`
- una formulazione piu ristretta puo fornire bounds duale (non ideali) utilizzabili in algoritmi branch-and-bound (algoritmi branch and cut)

Svantaggio:
- Non ci da garanzie su quanti passi ci vogliono per arrivare all'ottimo
- è necessaria una procedura apposita, `algoritmo di separazione`, per generare iterativamente disuguaglianze valide e utili
	- SE il problema è NP-hard, anche il problema di separazione lo è

Pseudo codice
Begin
//con $P$ il rilassamento continuo e $t$ indice dell'iterazione
t := 0; $P^{(0)}$ := $P$; 
repeat
	// risolvo il problema rilassato con $z^{*(t)}$ il valore ottimo e $x^{*(t)}$ la soluzione ottima
	$z^{*(t)} := max\{cx : x \in P^{(t)}\}$ 
	$x^{*(t)} := argmax\{cx : x \in P^{(t)}\}$ 
	if  $x^{*(t)} \notin Z^n$ then // soluzione ottima non intera
		genera un disuguaglianza valida $\pi x \leq \pi_0 : \pi x^{*(t)} > \pi_0$
		$P^{(t+1)} := P^{(t)} \cap \{x : \pi x \leq \pi_0\}$
		t := t+1
	end if
until $(x^{*(t)} \in Z^n)$ AND non riusciamo a trovare nessuna disuguaglianza valida (ANCHE SE esiste)
End

Dopo ogni iterazione, $z^{*(t)}$ è un bound duale valido che si avvicina sempre piu all ottimo

[[PLI - Tagli di Gomory]]