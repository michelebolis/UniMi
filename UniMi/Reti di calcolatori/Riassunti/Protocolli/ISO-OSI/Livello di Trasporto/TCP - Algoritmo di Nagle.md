Situazione: `produttore lento e consumatore veloce`
Lato destinazione è una variazione del delayed acknowledgement che aspetta SOLO un segmento che riceve l'ACK. Quando l'ACK arriva, tutti i caratteri nel buffer, vengono inviati in un unico segmento.

Lato produttore questo invia subito il primo segmento prodotto per tastare il terreno e misurare l'RTT quindi, ogni RTT tempo invia un pacchetto con tutti i chunk man mano prodotti

ES
Lato sender che produce 1B di dati ogni 20 msec., e con link avente banda di 100 Kbps e tempo di propagazione di 100 msec. 

Primo segmento 1B+20B = 21B
$t_x = \frac{21*8}{100000} = 1.68*10^{-3}$
$t_p= 100msec$
ack arriva dopo $1.68+2* 100 = 201.68msec$
In questo tempo sono stati prodotti $201.68/20 = 10$ B

Secondo segmento: 10B+20B = 30B
$t_x = \frac {30*8}{100000} = 2.4*10^{-3}$
ack arriva dopo $2.4 + 2*100 = 202.4msec$
In questo tempo sono stati prodotti $202.4/20 = 10B$

Terzo segmento (e tutti i successivi): 10B+20B = 30B