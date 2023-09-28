Un **GPIO (General Purpose Input/Output)** è la rappresentazione di un pin e del suo segnale digitale transitante. L'informazione passata dipende dalle tensione transitate su di esso alta/bassa.

Spesso è possibile scegliere se configurarli tramite software per associarli a qualche Intellectual Property o destinarlo come GPIO.

Tecniche per leggere lo stato di un pulsante:
* La resistenza è **pullup** quando si inserisce una resistenza tra il GPIO e l'alimentazione. Con questa tecnica SE il pulsante non è premuto lo stato logico è stabile a 1 in modo permanente. Lo si cambia premendo il pulsante.
* La resistenza è **pulldown** quando si inserisce una resistenza tra il GPIO e la massa