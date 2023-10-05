Per la definizione di un nuovo type, faccio un matching strutturale, in cui ogni caso è identificato da un nome con la prima lettera maiuscola, chiamato costruttore, eventualmente con un type specificato.

 ```ocaml
 type int_option = Nothing | AnInteger of int ;;
 let a = Nothing;; (*sarà: - : int_option = Nothing*)
 let a = AnInteger 7;; (*sarà: - : int_option = AnInteger 7*)
  ```

Sto definendo il dominio di una funzione con un pattern matching usando i costruttori

Se sto facendo piu definizioni contemporaneamente, uso l'`and`

es
 ```ocaml
 type card = Card of regular | Joker 
	 and regular = { suit : card_suit; name : card_name; } 
		 and card_suit = Heart | Club | Spade | Diamond 
		 and card_name = Ace | King | Queen | Jack | Simple of int;;
```
In questo esempio definisco `card` che o è `Card` o è `Joker`. 
`Card` sarà un record di tipo `regular` ma non avendolo definito uso l'$and$ per definirlo "inline".
La stessa cosa accade anche per `card_suit` e `card_name` che sono due tipi definiti "inline" con le Variants.

