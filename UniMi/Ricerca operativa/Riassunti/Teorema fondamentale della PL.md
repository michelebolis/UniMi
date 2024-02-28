Dato un problema lineare in [[Forma standard|forma standard]]
$$z = min\{c^T x : A*x = b, x>=0\} $$
Con $A$ di rango $m$

| Enunciato                                                                                | Interpretazione geometrica                                                                                                           |
| ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| SE esiste una `soluzione ammissibile`, esiste anche una `soluzione ammissibile di base ` | SE un poliedro non è vuoto, deve avere almeno un vertice                                                                             |
| SE esiste una `soluzione ottima`, esiste anche una `soluzione ottima di base`            | SE il poliedro non è illimitato verso la direzione di ottimizzazione, ci deve essere un vertice del poliedro che ha il valore ottimo |

Perciò `un problema lineare nel continuo può essere risolto come problema combinatorio discreto`, limitandosi a considerare solo le soluzioni di base.

[[Metodi risolutivi PL]]