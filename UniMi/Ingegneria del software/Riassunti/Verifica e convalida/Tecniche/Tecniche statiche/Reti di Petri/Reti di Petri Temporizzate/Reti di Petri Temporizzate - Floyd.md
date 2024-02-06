Per semplificare i vincoli è necessario esprimere i vincoli solo in termini della marcatura corrente
Algoritmo di Floyd
1. Si riconducono tutti i vincoli alla forma $A-B \leq k$ con $A$ e $B$ identificatori simbolici e $k$ una costante
2. Si costruisce una matrice in cui ad ogni riga e colonna corrisponde un identificatore simbolico e l'intersezione tra la riga $A$ e la colonna $B$ corrisponde al valore di $k$, che se non è noto si scrive $?$
3. Si riempiono tutti i posti contrassegnati da $?$ utilizzando la formula $$m[i,j] = m[i,k]+m[k,j]$$ in modo da scoprire i vincoli indiretti
4. Si esplicitano i vincoli indiretti relativi agli identificatori simboli presenti nella marcatura corrente, e si eliminano i vincoli che contengono gli identificatori non inclusi

Esempio
![[Pasted image 20240206105947.png|500]]
