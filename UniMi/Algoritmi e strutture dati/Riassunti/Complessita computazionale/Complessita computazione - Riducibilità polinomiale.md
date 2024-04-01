
$\pi_1$ è riducibile polinomialmente a $\pi_2, \pi_1 \leq_p \pi_2$, SE esiste riduzione $f: I_1 --> I_2$ calcolabile da un algoritmo $A_f$ in tempo polinomiale

```
ALGORITMO A1 (x ∈ I1) -> boolean //con n=|x|
y <- Af(x) //tempo p(|x|)
r <- A2(y) //tempo q(|y|)=q(|f(x)|)
RETURN r
```

Tempo totale $p(|x|) + q(|f(x)|) \leq p(|x|) + q(c*p(|x|)$
Perche $|f(x)| \leq c*p(|x|)$ ad ogni passo scrivo al piu $c$ caratteri in output
QUINDI $tempo \leq poly(|x|)$

Proprieta fondamentali:
- SE $\pi_1 \leq_p \pi_2$ e $\pi_2 \in P$ ALLORA $\pi_1 \in P$
- SE $\pi_1 \leq_p \pi_2$ e $\pi_2 \leq_p \pi_3$ ALLORA $\pi_1 \leq_p \pi3$

Es $SODD \leq_p CLIQUE$
