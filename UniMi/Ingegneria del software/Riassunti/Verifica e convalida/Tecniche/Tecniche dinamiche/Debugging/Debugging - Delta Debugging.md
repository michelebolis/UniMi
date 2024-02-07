- shrinking input: dato un input grande e complesso, strumenti automatici possono aiutare a ridurlo il piu possibile
- `Delta/Differential Debugging`: dato lo stesso input, i maniera automatica vengono esplorati  gli stati del programma mutando ad ogni iterazione piccole porzioni di codice

**`git bisect`** di Git: data una versione vecchia in cui il bug non è presente, una versione nuova in cui esso si è manifestato e un oracolo che stabilisce se il bug è presente o meno, Git esegue una **ricerca dicotomica** per trovare la versione che ha introdotto il problema