Il tempo è associato alle transizioni
Vengono associati degli insiemi di tempi di scatto possibili e definiti in maniera dinamica
Possono fare riferimento a tempi assoluti e ai tempi dei singoli gettoni

Informalmente
- I gettono non sono anonimi / timestamp
- Il tempo di abilitazione è il massimo tra i timestamp dei gettoni che compongono la tupla abilitante (enabling tuple)
- L'insieme dei tempi di scatto non possono essere minori del tempo di abilitazione: una transizione non puo scattare prima di essere abilitata
- Il tempo di scatto è uguale al quello scelto all'interno del set dei possibili e diventa timestamp di tutti i gettono prodotti

Una rete TB è una 6-tupla $<P, T, \theta ; F, tf, m_0>$
P, T; F sono come nelle reti di Petri normali
$\theta$  è un insieme numerico o dominio temporale
- $tf$ associa ad ogni transizione una funzione temporale $tf_t$ con $tf_t(en) \subseteq \theta$ e en è una tupla abilitante
- $m_0 : P -> \{(theta, mul(theta)) | theta\in \theta \}$, è un multiset che esprime la marcatura iniziale