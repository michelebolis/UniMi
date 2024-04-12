Voglio costruire una funzione che dato un evento mi restituisca la probabilita
$P: insiemeDiEventi --> R^+$
Vogliamo costruire una funzione coerente, devo poter considerare che avvenga un evento e che non avvenga un evento
[[Calcolo delle probabilità - Algebra degli eventi]]
$P$ non viene definito in modo diretto / operativo ma in modo indiretto / assiomatico
Una base di assiomi ha tutto e solo ciò che ci permette di dimostrare / ricavare qualcosa

[[Calcolo delle probabilità - Assiomi di Kolmogorov]]
Teoremi elementari:
- $E, F \in A, E \subseteq F, (E \implies F) \implies P(E) \leq P(F)$

DIM
$F= E \cup E' = E \cup (F - E)$
$P(F) = P(E) \cup P(E')$
$E \cap E' = \emptyset$ quindi posso applicare A3
$P(F) = P(E) + P(E')$
Usando A1, $P(E') \geq 0$, quindi $P(E) + P(E') \geq P(E)$

- $E \subseteq \Omega, P(E) \leq P(\Omega) = 1$ //per A2
- $P(\overline E) = 1 - P(E)$

La probabilita che un qualsiasi evento non si verifichi è pari a uno meno la probabilita che si verifichi
DIM
Considerando A2 (invertito), $1=P(\Omega)$
Considerando che $E \cup \overline E = \Omega$ e che $E \cap \overline E = \emptyset$
$1=P(E) \cup P(\overline E)$
$1=P(E) + P(\overline E)$ //perche sono eventi disgiunti applico A3
$1-P(E) = P(\overline E)$


$P(E \cup F)$ è possibile calcolarla con gli assiomi solo per eventi disgiunti
Nel caso più generale:
$P(E \cup F) = P(E) + P(F) - P(E \cap F)$
$P(E \cap F)$ viene sottratto perché contato due volte
DIM
$E - F= I = E \cap \overline F$
$E \cup F = II$
$F - E = III = F \cap \overline E$
Questi tre insiemi sono a due a due disgiunti

$E \cup F = I \cup II \cup III$
Essendo disgiunti vale A3
$P(E \cup F) = P(I) + P(II) + P(III)$

$I \cup II = E$
$II \cup III = F$
Applicando A3
$P(E) = P(I) + P(II)$
$P(F) = P(II) + P(III)$
$P(E \cup F) = P(E) + P(III)$
Aggiungo e sottraggo $P(II)$
$P(E \cup F) = P(E) + P(III) - P(II) + P(II)$
$P(E \cup F) = P(E) + P(F) - P(II)$

Stretto legame tra concetto empirico di frequenza e il concetto teorico di probabilita, entrambe si possono applicare ad un evento; la frequenza approssima la probabilita
Modelli parametrici: dipendono da 1 o piu parametri

[[Spazi degli esiti equiprobabili]]
[[Probabilità condizionata]]