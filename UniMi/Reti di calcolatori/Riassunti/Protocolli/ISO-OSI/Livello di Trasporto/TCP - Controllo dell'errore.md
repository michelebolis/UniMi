Manteniamo una variabile sia nel mittente che nel destinatario ($V_S$/$V_R$) con la `Initial Sequence Number`

TCP ritrasmette un segmento SOLO quando riceve 3 ACK duplicati per lo stesso segmento
Questo sistema funziona finche ho qualcosa da trasmettere, difatti non verra mai mandato un ACK al mittente. 
Per ogni trasmissione, un RTO inizia per il nuovo segmento 
Per ottimizzare è essenziale un'accurata [[Calibrazione RTO|calibrazione dell'RTO]]
Quando la ritrasmissione avviene prima dello scadere dell'RTO, in quanto ho ricevuto 3 ACK duplicati, si parla di `Fast Retrasmission`
[[Fast Retrasmission - Esempio]]