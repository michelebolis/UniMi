Sempre lancio di due dadi, ma so il risultato di un dado
È uscito 2 quale è la P che la somma sia 8? 1 / 6
La conoscenza del risultato mi ha fatto restringere omega

Probabilita condizionata: l'informazione parziale condiziona la probabilita
Dati due eventi $E, F \in A$, con $P(F) > 0$

Probabilità condizionata di $E$ dato $F$,
$$P(E|F) = \frac{P(E \cap F)}{P(F)}$$
$F$ è l'evento condizionante mentre $E$ è l'evento condizionato

SE si è verificato l'evento $F$, affinché si verifichi anche $E$, un suo elemento deve appartenere a $E \cap F$
Essendosi verificato $F$, questo evento diviene il nuovo spazio degli esiti

$(E \cap \overline F) \cup (E \cap F) = E$
$(E \cap \overline F) \cup (E \cap F) = E \cap (\overline F \cup F) = E \cap \Omega = E$ //abbiamo usato distributività
$(E \cap \overline F) \cap (E \cap F) = E \cap E \cap (F \cap \overline F) = E \cap \emptyset = \emptyset$ //abbiamo usato associatività e commutatività
QUINDI posso usare A3
$P(E) = P(E \cap \overline F) + P(E \cap F)$

Dalla formula della probabilità condizionata ricavo la regola di fattorizzazione
$$P(E \cap F) = P(E | F) * P(F)$$
La probabilità che $E$ e $F$ si verifichino entrambi è pari a quella che si verifichi $F$ per la probabilità condizionata di $E$ dato che si è verificato $F$

Supponendo di realizzare un numero molto elevato n di ripetizioni di un esperimento, $P(F)$ è il limite della frazione di prove in cui si verifica F, saranno circa $n*P(F)$ quelle in cui si verifica $F$ e analogamente $n*P(E \cap F)$
$$\frac{n*P(E \cap F)}{n*P(F)}=\frac{P(E\cap F)}{P(F)}$$
Le approssimazioni divengono esatte quando $n$ tende all'infinito

Siano $E$ e $F$ due eventi qualsiasi, $E= (E \cap F) \cup (E \cap \overline F)$
Considerando che $E \cap F$ e $E \cap \overline F$ sono eventi disgiunti
$P(E) = (E \cap F) + (E \cap \overline F)$
$= P(E | F) * P(F) + P(E | \overline F) * P(\overline F)$ //scrivo le intersezioni come moltiplicazioni
= //scrivo $P(\overline F)$ in funzione di $P(F)$
$$P(E)=P(E | F)*P(F)+P(E|\overline F)*(1-P(F))$$
La probabilità dell'evento $E$ si può ricavare come media pesata delle probabilità condizionate di $E$ sapendo che $F$ si è verificato e che non si è verificato

[[Teorema delle probabilità totali]]
[[Teorema di Bayes]]