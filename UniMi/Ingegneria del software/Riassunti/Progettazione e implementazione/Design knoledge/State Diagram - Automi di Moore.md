Un automa è una n-upla $<S, I, U; δ, t, s_0>$ con
- $S$ l'insieme finito e NON vuoto degli stati
- $I$ l'insieme finito dei possibili ingressi
- $U$ l'insieme finito delle possibili uscite
- δ la funzione di transizione, $δ: S \text{ x } I -> S$
	- Dato uno stato ed un segnale di input, stabilisce quale è il prossimo stato 
	- Può essere una funzione parziale (potrebbe non esistere un prossimo stato data una certa coppia)
- t la funzione di uscita, t: S -> U
- $s_0$ lo stato iniziale con $s_0 \in S$

[[Automi di Mealy]]