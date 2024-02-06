Introdotte nel 1989 da `Ghezzi`
Vengono associati degli `insiemi variabili` di `tempi di scatto assoluti` possibili e definiti in maniera dinamica
Possono fare riferimento sia a tempi assoluti che ai tempi dei singoli gettoni

Informalmente
- I gettono non sono anonimi ma caratterizzati da un timestamp, cioè il momento in cui sono stati creati
- Il tempo di abilitazione, cioè il momento in cui la transizione viene abilitata, è il massimo tra i timestamp dei gettoni che compongono la tupla abilitante (enabling tuple)
- L'insieme dei tempi di scatto non possono essere minori del tempo di abilitazione: una transizione non puo scattare prima di essere abilitata
- Il tempo di scatto è uguale al quello scelto all'interno del set dei possibili e diventa timestamp di tutti i gettono prodotti

Una rete TB è una 6-tupla $<P, T, \Theta ; F, tf, m_0>$
- $P, T; F$ sono come nelle reti di Petri normali
- $\Theta$  è il `dominio temporale`, cioè l'insieme numerico che contiene le rappresentazioni degli istanti di tempo
- $tf$ è una funzione che associa ad ogni transizione una funzione temporale $tf_t$ che, data in input una tupla abilitante $en$, restituisce un insieme di tempi di scatto possibili,  $$tf_t(en) \subseteq \Theta$$es data una transizione t con tempi di scatto in $[min, max]$, $tf_t(en)=r|min \leq r \leq max$
- $m_0$, è un multiset che esprime la marcatura iniziale, in particolare è una funzione che associa ad ogni posto, un insieme di coppie timestamp-molteplicità  $$m_0 : P -> \{(\theta, mul(\theta)) | \theta\in \Theta \}$$
Il concetto di tempo è difficile da definire in maniera univoca.
Esistono quindi per reti TB diverse semantiche temporali: [[Reti di Petri Temporizzate - Tipi di semantiche temporali]]