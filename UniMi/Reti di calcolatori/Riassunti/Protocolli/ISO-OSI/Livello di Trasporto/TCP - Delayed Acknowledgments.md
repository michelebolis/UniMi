Per ridurre il numero di segmenti inviati, TCP NON ritorna immediatamente l'ACK quando riceve un segmento senza errori MA aspetta, tipicamente 200ms, per vedere se ci sono dati che vengono messi nel buffer send: `Delayed Acknowledgments`
Quindi il segmento avra $PSH=1$, $ACK=1$, $ACK=X+1$, $SEQ=Y$, Data='d'

MA viene aggiunto cosi del delay aggiuntivo in cui si aspetta che l applicazione debba inviare qualcosa
Soluzione: [[TCP - Algoritmo di Nagle]]