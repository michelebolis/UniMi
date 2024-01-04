Come inviare dati continuamente (es Secure Shell)
in questi casi hanno nel segmento PSH=1
Lato ricevente, una volta ricevuto il dato, oltre il segmento con ACK, viene mandato un altro segmento al mittente con PSH=1 con lo stesso dato che ha ricevuto

MA è inefficiente
Soluzione: [[TCP - Delayed Acknowledgments]]
