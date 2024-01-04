La congestione è un fattore della rete determinato dal riempimento delle code nei router e causa della perdita di segmenti

TCP rileva la congestione come un errore di trasmissione
- thougthput: utilizzo del canale nel tempo
- goodput: thougthput - utilizzo canale per ritrasmissioni

l obiettivo del TCP quando viene utilizzato per l invio di grandi quantita di dati, è mandare in parallelo piu segmenti possibili

Ipotizziamo di avere la trasmissione di segmenti verso una destinazione in cui in un primo tratto, ho una trasmissione veloce MA poi dal router alla destinazione ho un canale lento (collo di bottiglia). 
SE la rete ce la fa, si nota solo un aumento di RTT RoundTripTime
SE i buffer del router si saturano, elimina i segmenti e TCP rileva l'errore di trasmissione MA la sorgente come stima quanti segmenti inviare nell'unita di tempo?

La finestra di congestione indica quanti byte si possono immettere nella rete 
La sorgente sa che se invio un segmento e ne ricevo l'ACK, allora il segmento ha lasciato la rete 
L'unica cosa sicura è l'ACK arrivano con il tempo piu lento della rete, essendo di piccole dimensioni
[[Dimensionamento della finestra di congestione]]

