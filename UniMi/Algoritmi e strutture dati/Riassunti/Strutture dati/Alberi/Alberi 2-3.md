DEF Un albero 2-3 è un albero in cui
- Ogni nodo interno ha 2 o 3 figli
- Tutte le foglie si trovano allo stesso livello

Relazione tra i nodi/foglie e l'altezza
Fissata h l'altezza dell'albero
- Minimo $n$ nodi: albero binario completo
	- Numero nodi: $2^{h+1} -1$
	- Numero foglie: $2^h$
- Massimo $n$ nodi: albero ternario completo
	- Numero nodi: $\frac{3^{h+1} -1}{2}$
	- Numero foglie: $3^h$

SE $n$ foglie: $\log_3 n\leq h \leq \log_2 n$
$h=\Theta(\log n)$

Nelle foglie ci sono le informazioni in ordine non decrescente da sx a dx
Nei nodi interni invece ho delle chiavi di instradamento:
- SE nodo ha 2 figli, contiene la chiave piu grande del sottoalbero sx
- SE nodo ha 3 figli ho 2 chiave, la chiave piu grande del sottoalbero SX e la chiave piu grande del sottoalbero centrale
Chiavi inserite in fase di inserimento

Come informazione base ho il puntatore alla radice
Numero di passi per la ricerca dipende da $h$, che essendo logaritmica è $\Theta(\log n)$
Implementata considerando 2 tipi di nodi
- Foglie: che contengono la chiave e altri campi
- Nodi interni: contengono i 3 puntatori ai figli e la chiave piu grande del sottoalbero sx e la chiave piu grande del sottoalbero centrale
OSS è utile per inserimenti/cancellazioni avere un puntatore al padre

Inserimento situazioni possibili:
- Inizio con la fase di ricerca fino a che non arrivo ad una foglia. SE nodo interno ha 2 figli lo aggiungo perché c è spazio
- SE pero il nodo interno ha già 3 figli, faccio un operazione di split, dividendo i 4 figli in 2 gruppi da 2 procedendo verso l'alto in quanto non posso avere piu di 4 nodi interni. Continuo cosi finché non ottengo un albero 2-3 eventualmente facendo split anche della radice

Durante l'inserimento la crescita di altezza avviene verso la radice, non verso il basso

Supponiamo di avere un elenco di chiavi. La prima sarà la radice
Per la cancellazione se nodo ha un figlio faccio merge con uno vicino

|               | Alberi 2-3 | Alberi AVL | Perfettamente bilanciati |
| ------------- | ---------- | ---------- | ------------------------ |
| Ricerca       | Θ(lg n)    | Θ(lg n)    | Θ(lg n)                  |
| Inserimento   | Θ(lg n)    | Θ(lg n)    | Θ(n)                     |
| Cancellazione | Θ(lg n)    | Θ(lg n)    | Θ(n)                     |

es
![[Pasted image 20240401134547.png]]