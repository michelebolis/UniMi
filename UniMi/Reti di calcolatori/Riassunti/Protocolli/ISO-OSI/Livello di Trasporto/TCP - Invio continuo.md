Come inviare dati continuamente (es Secure Shell)
in questi casi hanno nel segmento PSH=1
Lato ricevente, una volta ricevuto il dato, oltre il segmento con ACK, viene mandato un altro segmento al mittente con PSH=1 con lo stesso dato che ha ricevuto

MA è inefficiente

Delay ACK, SE il ricevente ha qualcosa da inviare, mando sia il dato che l'ACK del segmento precedente.
Quindi il segmento avra PSH=1, ACK=1, Ack=X+1, SEQ=Y, Data='d'

MA viene aggiunto cosi del delay aggiuntivo in cui si aspetta che l applicazione debba inviare qualcosa