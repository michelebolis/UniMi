DEF un albero binario è detto bilanciato in altezza quando per ogni nodo la differenza in valore assoluto tra le altezze dei suoi sottoalberi sinistro e destro è al massimo 1
SE è perfettamente bilanciato, allora è anche bilanciato in altezza

Relazione $n$ nodi e $h$ altezza
N minimo di nodi
$h=0, n=1$
$h=1, n=2$
$h=2, n=4$
$h=3, n=7$

L'albero $T_h$ lo ottengo prendendo i 2 alberi AVL precedenti
Per $h$ generico $T_h$, è formato da $T_{h-1}$ a sinistra e $T_{h-2}$ a destra
Questi si chiamano alberi di Fibonacci di altezza $h$
Proprietà è un albero AVL di altezza $h$ con minimo numero di nodi
$$n_h= \begin{cases}1 \text{ SE } h=0 \\ 2 \text{ SE } h=1 \\ 1+n_{h-1}+n_{h-2} \end{cases}$$
$n_h= F_{h+3} -1$
…
$F_n \approx \frac{\phi ^n}{\sqrt{5}}$ con $\phi=1,618…$
$n_h = \frac{\phi ^{h+3}}{\sqrt{5}} -1 \approx \frac{\phi ^{h+3}}{\sqrt{5}}$
$\sqrt{5} * n_h \approx \phi^{h+3}$
$h+3 \approx \log \phi\sqrt{5} * n_h$
$h+3 \approx \log \phi\sqrt{5} + \log\phi n_h$
$h = \theta(\log n)$
$h <1,44*\log n$

Proprietà ogni albero AVL ha altezza h con $h=\theta(\log n)$
Con l'inserimento gli AVL si possono sbilanciare ma il costo per sistemarli è minore
- Sbilanciamento a SX nel sottoalbero SX --> rotazione a DX di perno A, faccio salire B facendo risalire l albero SX di 1 e la radice A scendono di 1 a DX unendo il sottoalbero DX di B a SX di A
Ho costo costante 3
- Sbilanciamento a DX nel sottoalbero SX
	- Rotazione a SX di perno B, B scende mentre C sale al posto di B
	- Rotazione a DX di perno A, quindi C sale come radice mentre A scende a DX mettendo nel suo sottoalbero di SX il sottoalbero DX di C
Il ribilanciamento può essere fatto in tempo costante

es
![[Pasted image 20240401133439.png]]

|               | Alberi AVL       | Perfettamente bilanciati |
| ------------- | ---------------- | ------------------------ |
| Ricerca       | $\Theta(\log n)$ | $\Theta(\log n)$         |
| Inserimento   | $\Theta(\log n)$ | $\Theta(n)$              |
| Cancellazione | $\Theta(\log n)$ | $\Theta(n)$              |
