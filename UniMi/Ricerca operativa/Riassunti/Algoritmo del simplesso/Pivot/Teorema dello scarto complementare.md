- $P$: maximize $z=c^Tx$, s.t. $Ax\leq b$, $x \geq 0$
- $D$: minimize $w=b^Ty$, s.t. $A^Ty \geq c$, $y \geq 0$

`Condizione necessaria e sufficiente per l'ottimalità di due soluzioni ammissibili` $\bar{x}$ e $\bar{y}$ è che valgano le equazioni seguenti
$$\bar{y}^T(b-A\bar{x}) = 0$$
$$(A^T\bar{y} - c)\bar{x} = 0$$

OSS stiamo usando la forma alle disuguaglianze, per i vincoli di uguaglianza sono già implicate dall'ammissibilità delle soluzioni.