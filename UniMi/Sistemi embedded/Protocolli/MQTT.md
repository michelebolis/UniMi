*MQTT (Message Queuing Telemetry Transport)*: protocollo del tipo publisher/subscriver (obesrver/observee) basato su messaggi. I messaggi fomrati da *topic* (parole separate da "/") e *payload* (stringa UTF-8) sono inviati da un nodo *client*  ad un *broker* al quale sono connessi. Il *broker* broadcasta il messaggio a tutti i nodi che si sono iscritti a quel *topic*. I nodi che ricevono il messaggio eseguiranno una funzione callback definita da loro.
 Funzioni da nodo connesso a broker

 ```c++
 Subscribe(String subTopic, Function callback)
 
 Publish(String topic, String message)
 ```
