```c
while (!Infeasible(b,c)) AND (!FeasibleBase(b)) do
	Pivot(A,b,c)
if Infeasible(b, c) then
	"Stop: problema inammissibile"
else 
	while (!Optimal(c)) AND (!Unbounded(A, c)) do
		Pivot(A, b, c)
	if Optimal(c) then 
		"Stop: soluzione ottima"
	else 
		"Stop: problema illimitato"
```

1. `Si trova una soluzione di base ammissibile`.
	 `While finche la base non è Ammissibile e non abbiamo dimostrato che il problema è inammissibile`
	L'iterazione fondamentale del simplesso è il Pivot step
2. SE il problema è inammissibile, allora l'algoritmo termina
3. `Si cerca una soluzione ottima`
	`Ogni iterazione conserva l'ammissibilità`
	Possibilità:
	- Si trova la `soluzione ottima` 
	- Si scopre che il `problema è illimitato`

Infeasible = Test che verifica che la base sia ammissibile
Unbounded = Test che verifica che il problema sia illimitato

Parti:
- [[Pivot(A, b, c)]]