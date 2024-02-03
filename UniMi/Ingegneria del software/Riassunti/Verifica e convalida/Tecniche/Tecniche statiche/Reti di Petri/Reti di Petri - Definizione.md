Una rete di Petri è una quintupla $[P, T;F,W,M_0]$ con:
- $P$ l'insieme degli `identificatori dei posti`
- $T$ l'insieme degli `identificatori delle transizioni`
- $F$ la `relazione di flusso` t.c. $F \subseteq (P \text{ x } T) \cup (T \text{ x } P)$
- $W$ la `funzione peso` t.c. $W: F -> N^+$
- $M_0$ la `funzione marcatura iniziale` t.c. $M_0: P -> N^+$

In generale una `marcatura` è una particolare configurazione dell'assegnamento dei gettoni in una rete di Petri
Proprietà: $P \cap T = 0$

Definiamo
Il `preset` di un nodo $a$ è l'insieme degli elementi appartenenti all’unione degli insiemi degli identificatori di posti e transizioni tali che esiste una relazione di flusso tra $d$ e $a$ appartenente a $F$. In sostanza l'`insieme degli identificatori antecedenti` ad $a$
$$pre(a) = \{d \in (P \cup T) | <d, a> \in F\}$$
Il `postset` di un nodo $a$ è l’insieme degli elementi $d$ appartenenti all’unione degli insiemi degli identificatori di posti e transizioni tali che esiste una relazione di flusso tra $a$ e $d$ appartenente a $F$. In sostanza l'`insieme degli identificatori successivi` ad $a$
$$post(a) = \{d \in (P \cup T) | <a, d> \in F\}$$

[[Reti di Petri - Comportamento dinamico]]
Definiamo poi:
- [[Reti di Petri - Insieme di raggiungibilità|Insieme di raggiungibilità]]
- [[Reti di Petri - Rappresentazione matriciale]]
