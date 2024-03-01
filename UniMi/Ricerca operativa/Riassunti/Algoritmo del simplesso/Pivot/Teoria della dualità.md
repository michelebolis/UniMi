E' il fondamento su cui si possono progettare algoritmi di ottimizzazione e di approssimazione e dimostrare le loro proprietà
Ogni problema di PL, il problema primale, ammette un altro problema di PL, problema duale

| Problema primale                              | Problema duale                             |
| --------------------------------------------- | ------------------------------------------ |
| Minimizzazione                                | Massimizzazione                            |
| $m$ vincoli                                   | $m$ variabili                              |
| $n$ variabili                                 | $n$ vincoli                                |
| i coefficienti della f.o. diventano           | i termini noti dei vincoli                 |
| i termini noti dei vincoli diventano          | i coefficienti della f.o.                  |
| matrice dei coefficienti A                    | matrice dei coefficienti $A^T$ (trasposta) |
| ogni vincolo di uguaglianza diventa           | una variabile libera                       |
| ogni variabile libera diventa                 | un vincoli di uguaglianza                  |
| ogni vincolo di disuguaglianza $\geq$ diventa | una variabile non negativa                 |
| ogni variabile non negativa diventa           | un vincolo di disuguaglianza $\leq$        |

---

| Problema primale P              | Problema duale D                    |
| ------------------------------- | ----------------------------------- |
| minimize $z=c_1^Tx_1+c_2^Tx_2$  | maximize $w=b_1^Ty_1+b_2^Ty_2$      |
| $A_{11}x_1 + A_{12}x_2\geq b_1$ | $A^T_{11}y_1 + A^T_{21}y_2\leq c_1$ |
| $A_{21}x_1 + A_{22}x_2 = b_2$   | $A^T_{12}y_1 + A^T_{22}y_2 = c_2$   |
| $x_1\geq 0$                     | $y_1\geq 0$                         |
| $x_2$ libera                    | $y_2$ libera                        |
La relazione è simmetrica: quindi il duale del duale di P è P

Teoremi
- [[Teorema della dualità in forma debole]]
- [[Teorema fondamentale dell'algebra]]
- [[Lemma di Farkas]]
- [[Teorema della dualità in forma forte]]
- [[Teorema fondamentale della dualità lineare]]