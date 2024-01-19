Situazione: `produttore lento e consumatore veloce`
Lato destinazione è una variazione del delayed acknowledgement che aspetta SOLO un segmento che riceve l'ACK. Quando l'ACK arriva, tutti i caratteri nel buffer, vengono inviati in un unico segmento.

Lato produttore questo invia subito il primo segmento prodotto per tastare il terreno e misurare l'RTT quindi, ogni RTT tempo invia un pacchetto con tutti i chunk man mano prodotti