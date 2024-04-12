SE $P(E | F) = P(E)$, sapere che $F$ si sia verificato non cambia la quantificazione dell'incertezza di $E$, diciamo che i due eventi sono indipendenti.

$$P(E|F)= P(E)\iff\frac{P(E\cap F)}{P(F)} =P(E)$$$$P(E \cap F) = P(E) * P(F)$$
$$P(F|E)=P(F)\iff\frac{P(E\cap F)}{P(E)}=P(F)$$$$P(F \cap E) = P(E) * P(F)$$
SE $E$ è indipendente da $F$, $F$ è indipendente da $E$

SE so che due eventi sono indipendenti, allora anche tutti gli eventi che compongo da essi sono indipendenti
SE $E$ e $F$ sono indipendenti, lo sono anche $E$ e $\overline F$
DIM $E, F$ indipendenti $\implies$ $E, \overline F$ indipendenti
$P(E \cap F) = P(E)*P(F)$
Ipotesi $P(E \cap \overline F) = P(E)*P(\overline F)$

$E= (E \cap F) \cup (E \cap \overline F)$
Uso A3 perché sono disgiunti
$P(E) = P(E \cap F) + P(E \cap \overline F)$
$P(E \cap \overline F) = P(E) - P(E \cap F)$
$P(E \cap \overline F) = P(E) - P(E)*P(F)$
$P(E \cap \overline F) = P(E)*(1-P(F)) = P(E)*P(\overline F)$

Estendiamo il concetto di indipendenza a più di 2 eventi
Fallace pensare gli eventi a due a due
$E, F, G$ indipendenti $\iff$ $P(E \cap F) = P(E) * P(F), P(E \cap G) = P(E) * P(G), P(F \cap G) =$
$P(F) * P(G), P(E \cap F \cap G) = P(E) * P(F) * P(G)$

DIM $E, F, G$ indipendenti $\implies$ $E, F \cup G$ indipendenti
$P(E \cap (F \cup G))$
$= P( (E \cap F) \cup (E \cap G) )$ //= proprietà distributiva
$= P(E \cap F) + P(E \cap G) - P( (E \cap F) \cap (E \cap G) )$ //= non so se sono disgiunti, applico formula generale
$= P(E \cap F) + P(E \cap G) - P( E \cap F \cap G )$ //$P( (E \cap F) \cap (E \cap G) = E \cap F \cap G$ usando associatività e commutatività
$= P(E)*P(F) + P(E)*P(G) - P(E)*P(G)*P(F)$ //= sfrutto tesi
$= P(E)*(P(F) + P(G) - P(F)*P(G) )$ //= metto a fattore comune $E$
$= P(E)*(P(F) + P(G) - P(F \cap G) )$ //= uso indipendenza al contrario
$= P(E)*P(F \cup G)$ //= tra parentesi ho l unione $F \cup G$

QUINDI $P(E \cap (F \cup G)) = P(E)*P(F \cup G)$

Generalizzazione:
Gli eventi $E_1, …, E_n$ si dicono indipendenti SE per ogni loro sottogruppo $E_{a_1}, …, E_{a_r}$ con $1\leq a_1\leq …\leq a_r\leq n$ vale l'equazione:
$$P(\bigcup_{i=1}^r E_{ai})=\prod_{i=1}^r P(E_{a_i})$$
È ragionevole assumere che gli esiti di qualunque gruppo di queste prove non influenzino quelli delle altre
In questo caso gli eventi che dipendono dai singoli sotto esperimenti sono indipendenti e l'intero ambito si dice schema delle prove indipendenti
Almeno --> vale la pena complementare