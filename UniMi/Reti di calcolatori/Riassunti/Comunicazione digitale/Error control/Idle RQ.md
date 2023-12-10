Questo schema viene anche chiamato send-and-wait o stop-and-wait
Opera in modalità half-duplex

Il mittente invia solo un I-frame alla volta, facendo partire un timer ogni volta che ne invia uno.
- Il ricevente informa il mittente della corretta ricezione del frame con un acknowledgment o ACK-frame, in modo che il mittente resetti il timer e invii il successivo.
- SE l'I-frame contiene degli errori, viene inviato un negative acknowledgment o NAK-frame, in modo che il mittente proceda ad inviarne un altra copia, restartando il timer.
- SE invece P non riceve l'ACK entro lo scadere del timer, P ritrasmette l'I-frame di cui stava aspettando l'ACK. Il destinatario riconosce che il frame ricevuto è un duplicato e provvede a scartarlo e a mandare l'ACK del frame.

Per fare in modo che il destinatario determini che il frame ricevuto sia o meno un duplicato, ogni frame contiene un identificativo numerico di sequenza come anche ogni ACK associato all'i-esimo frame

NACK non piace perché è un messaggio di controllo in piu e perché non serve a molto inducendo un ACK con semantica selettiva 