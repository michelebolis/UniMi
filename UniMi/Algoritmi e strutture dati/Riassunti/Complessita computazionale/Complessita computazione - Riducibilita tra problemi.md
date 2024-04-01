Dati due problemi di decisione
- $\pi_1: I_1 --> \{0, 1\}$
- $\pi_2: I_2 --> \{0, 1\}$
$\pi_1$ è riducibile a $\pi_2$ SE esiste $f: I_1 --> I_2, \forall x \in I_1$ QUINDI $\pi_1(x)=\pi_2(f(x))$

```
ALGORITMO A1 (x ∈ I1) -> boolean
y <- f(x)
r <- A2(y) //con A2 un algoritmo per 𝜋2
RETURN r
```
