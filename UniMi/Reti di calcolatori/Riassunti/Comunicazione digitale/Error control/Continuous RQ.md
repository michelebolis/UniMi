Opera in modalità duplex

Il mittente invia I-frame in modo continuativo senza aspettare il ritorno di un ACK. Il mittente conserverà quindi una copia dell'I-frame trasmesso in un lista di ritrasmissione. 
Il destinatario anche in questo caso invierà un ACK per ogni frame ricevuto correttamente, conservandolo in una lista di ricezione. Anche in questo caso sarà necessario avere nei frame e negli ACK un numero di sequenza identificativo
Alla ricezione del ACK, viene rimosso dalla lista il corrispettivo frame

Il mittente conserva una variabile di sequenza N(S) che indica il prossimo frame da trasmettere
Il destinatario invece conserva una variabile di sequenza V(R) che indica il prossimo frame che sta aspettando

Strategie di ritrasmissione:
- [[Selective repeat]]
- [[Go back-N]]
