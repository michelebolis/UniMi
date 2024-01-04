SE RTO scade, NON ho ricevuto l'ACK
La congestione è molto grave in quanto lo scadere del RTO è calcolato come un evento raro

Quando scade l'RTO, si riparte con $W_C = 1$ quindi con uno slow start MA la SlowStartThreshold viene diminuita (in particolare alla meta della finestra in cui è scaduta l'RTO)