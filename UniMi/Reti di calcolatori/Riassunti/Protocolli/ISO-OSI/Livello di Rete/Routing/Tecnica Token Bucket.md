Utilizzato per garantire i requisiti di banda, delay e Jitter
Ad ogni flusso viene associato un contenitore, bucket, di token che vengono immessi ad un rate determinato dalla larghezza di banda richiesta

La dimensione del bucket è la stessa del massimo spazio della coda
In questo modo SE ci sono sufficienti token, il pacchetto è messo in coda e il corrispondente numero di token viene prelevato mentre SE non ci sono abbastanza token, il pacchetto viene scartato (perché sto andando ad un Rate superiore)

La coda che va in overflow eventualmente sarà quella di input