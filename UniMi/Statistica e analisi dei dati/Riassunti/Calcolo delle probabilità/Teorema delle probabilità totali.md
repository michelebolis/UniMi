Consideriamo partizioni di $\Omega$ $F_i$ t.c. $\bigcup_{i=1}^nF_i=\Omega$ con $\forall i, j, i \neq j, F_i \cap F_j = \emptyset$
$$P(E)=\sum_{i=1}^n P(E|F_i)*P(F_i)$$
In questo caso ho una serie di eventi condizionanti e non ho piu il complemento
DIM
$E= \bigcup_{i=1}^n (E \cap F_i) = E \cap (\bigcup_{i=1}^n F_i) = E \cap \Omega = E$
$(E \cap F_i) \cap (E \cap F_j) = \emptyset$ lo dimostro $E \cap E \cap F_i \cap F_j = \emptyset$ con $F_i\neq F_j$
$P(E) = \sum_{i=1}^n P(E \cap F_i) = \sum_{i=1}^n P(E | F_i) * P(F_i)$