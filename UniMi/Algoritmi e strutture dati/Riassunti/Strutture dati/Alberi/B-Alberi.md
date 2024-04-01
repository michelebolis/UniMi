DBMS Data Base Management System
Uso di indici per garantire accesso veloce ai dati. E' possibili piu indici basati su campi differenti
Gli indici possono essere molto grandi e quindi a causa della loro dimensione potrebbero non essere caricati in memoria centrale
Si possono realizzare strutture ad albero per implementare dizionari in memoria secondaria tenendo conto di vincoli tecnici

MA l'accesso ai dati è piu lento che in memoria centrale
Effettuiamo quindi un accesso a blocchi o pagine cosi da ottenere piu dati tipicamente di dimensione 29 o 212
Il nostro obiettivo è di minimizzare il numero di accessi alla memoria di massa

DEF un B-albero di ordine $t$ (cioè grado minimo $t$) è un albero $T$ t.c.
- Ogni nodo interno ha al massimo $2t$ figli
- Ogni nodo interno diverso dalla radice ha almeno $t$ figli
- La radice ha almeno 2 figli
- Tutte le foglie si trovano allo stesso livello
- Ogni foglia contiene $k$ chiavi ordinate $a_1\leq…\leq a_k$ dove $t-1 \leq k \leq 2t-1$
- Ogni nodo interno con $k+1$ figli e sottoalberi $T_0, …, T_k$ contiene $k$ chiavi ordinate $a_1\leq…\leq a_k$ t.c. per ogni chiave $c_i$ di $T_i$ con $i=0, …, k$ risulta $c_0\leq a_1\leq c_1\leq a_2\leq …\leq c_{k-1}\leq a_k$

es
![[Pasted image 20240401134946.png]]

Devo fare ricerca nel singolo nodo, uno alla volta
Organizzando i nodi come array posso fare un ricerca binaria: $O(\log t)$ considerando che ho al massimo $2t$ chiavi
SE non trovo la chiave nel nodo devo scendere in un nodo del sottoalbero, dovendo continuare al massimo l'altezza dell'albero+1 volte
Numero totale di passi $\Theta(h*\log t)$

SE ci sono $n$ chiavi, quanto può essere al massimo $h$?

| h   | # minimo nodi | n minimo chiavi                                                            |
| --- | ------------- | -------------------------------------------------------------------------- |
| 0   | 1             | 1                                                                          |
| 1   | Precedente+2  | Precedente+2                                                               |
| 2   | …+2t          | …+2t*(t-1)                                                                 |
| 3   | $…+2t^2$      | $…+2t^2*(t-1)$                                                             |
| …   |               |                                                                            |
| h   | $2t^{h-1}$    | $2t^{h-1}*(t-1)$                                                           |
| TOT |               | 1+2(t-1)* ∑ i=0 a h-1 ti<br>1+2(t-1)* (t2-1) / (t-1)<br>1+2th -2<br>2th -1 |

$n>= 2t^{h -1}$
$\frac{n+1}{2} \geq t^h$
$h \leq \frac{(\log _t n+1)}{2}$

Ricerca $\Theta(h*\log t)=h*\log _b t \leq \frac{(\log_t n+1)}{2} * \log_b t= \frac{(\log_b n+1)}{2}$
Numero passi di ricerca $\Theta(\log n)$
È indipendente da $t$

La scelta di $t$ è importante per il numero di accessi alla memoria, che voglio minimizzare
SE sono sicuro che ogni nodo necessita di un unico accesso a disco, il numero di accessi a disco è pari all'altezza dell'albero quindi $\frac{\log_t n+1}{2} \approx \log_t n$
SE uso alberi AVL il numero di accessi è circa $\log_2 n$
SE uso alberi 2-3 il numero di accessi è circa $\log_2 n$

Inserimento
- Ricerca la foglia (per garantire consistenza) in cui l'elemento va inserito
- SE c è spazio nella foglia, inserisci l'elemento al posto giusto in un array ordinato $O(t)$
- SE non c è spazio quindi ho $2t$ elementi, considero ancora una tecnica di split dividendo la foglia in due foglie, $t-1$ elementi e $t$ elementi, inserendo la chiave nuova nel nodo sopra

| A                         | Tempo              | Numero di accessi alla memoria di massa               |
| ------------------------- | ------------------ | ----------------------------------------------------- |
| Ricerca                   | $\Theta(\log n)$   | $\approx \log_t n$                                    |
| Inserimento/cancellazione | $\Theta(t*\log n)$ | $\approx C*\log_t n$ //C dipende dall'implementazione |

es
![[Pasted image 20240401135758.png]]