I link sono simmetrici; per ottenere link asimmetrici si utilizzano i monitor
SE A monitora B, quando B muore A riceverà un segnale di uscita MA SE A muore, B non riceverà un segnale

Creazione di un monitor per un processo A su un B: `erlang:monitor(process, B)`
Quando B muore con segnale di uscita Reason, `{'Down', Ref, process, B, Reason}` viene mandato a A, con Ref il riferimento al monitor