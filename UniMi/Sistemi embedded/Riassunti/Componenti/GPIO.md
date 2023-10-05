Un **GPIO (General Purpose Input/Output)** è la rappresentazione di un pin e del suo segnale digitale transitante. L'informazione passata dipende dalle tensione transitate su di esso alta/bassa.

Tipi di GPIO
* **digitali**: accettano 2 valori: 1 HIGH, 0 LOW
* **analogici**: gestiscono diversi livelli di tensione tra 0V e 5V trasformando tale tensione in un valore tra 0-255 grazie al circuito interno di digital-to-analog converter DAC

Spesso è possibile scegliere se configurarli tramite software per associarli a qualche Intellectual Property o destinarlo come GPIO.

Tecniche per leggere lo stato di un pulsante:
* La resistenza è **pullup** quando si inserisce una resistenza tra il GPIO e l'alimentazione. Con questa tecnica SE il pulsante non è premuto lo stato logico è stabile a 1 in modo permanente. Lo si cambia premendo il pulsante.
* La resistenza è **pulldown** quando si inserisce una resistenza tra il GPIO e la massa

Altri piedini:
* [[PWM]] (Pulse With Modulation): è possibile fornire una tenzione variabile. Nell'Arduino Uno i GPIO adibiti all'uso di PWM sono quelli con la tilde (~).

	analogWrite(11, 100):
	- Primo parametro (11) --> GPIO dell'Arduino Uno
	- Secondo parametro (100) -->  Valore che può andare da 0 a 255 per la generazione dell'onda quadra ().
* AREF (Analog REFerence): pin per fornire in input la tensione da usare come riferimento per l'analog input