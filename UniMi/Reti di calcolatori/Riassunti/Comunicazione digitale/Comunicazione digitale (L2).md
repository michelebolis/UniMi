In ogni sistema finale vi è una NIC network interface card, un HW controllato dal relativo SW che esegue le funzioni di rete

La rete deve essere in grado di riconoscere se un pacchetto è corretto/non alterato e rimediare all errore. SE la rete è affidabile e succedono degli errori, siamo in grado di risolverli dagli host (non dalla rete). [[Controllo dell'errore (L2)]]

Nel caso in cui il pacchetto sia arrivato corretto, ma la consegna dei singoli pacchetti non è in ordine, è necessario un meccanismo per ricomporli. In particolare oltre a sorgente e destinazione, si puo avere una serie di bit per riconoscere la posizione del pacchetto nella sequenza e la lunghezza totale della sequenza. Potrò quindi anche riconoscere se ho ricevuto dei duplicati

[[Trasmissione in banda base]]
[[Modalita di comunicazione]]
[[Sliding window]]
[[HDLC]]