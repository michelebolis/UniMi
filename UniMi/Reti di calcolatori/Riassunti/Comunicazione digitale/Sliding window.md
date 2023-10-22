Esso prevede di impostare un numero massimo di frame di cui posso aspettare un ACK, questo limite è detta finestra k.
SE k=1, stiamo usando un idle RQ

Idle RQ e go-back N necessitano solo di un buffer mentre per il selective repeat sono necessari k frame. 

Numero di identificatori necessari:
- Idle RQ: le finestre di ricezione e invio sono entrambe 1.
- Go back N: data una finestra di K, il numero di identificatori deve essere di almeno k+1 in quanto con k usato, il ricevente non sarebbe in grado di determinare se il un frame ricevuto sia nuovo o il duplicato del precedente
- Selective repeat: data una finestra di k, il numero di identificato deve essere di almeno 2k, in quanto nel caso peggiore in cui vengano inviati k frame e tutti gli ACK siano corrotti, il destinatario deve essere in grado di determinare se uno dei successivo k frame sia un nuovo frame.