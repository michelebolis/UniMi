Le linee di accesso usano tutte una trasmissione seriale bit a bit (da LSB a MSB).
Il segnale in output dalla NIC varia tra due livello di voltaggio \[-V; +V], secondo un bit rate
Considerando -V per lo 0 e +V per l'1.

Uso un `modulatore`, un device che modula un onda sinusoidale per darle una forma approssimata, a banda limitata cioe considerando un certo numero di armoniche (ognuna una frequenza in Hz). 
Se uso poca banda (poche armoniche), la forma del segnale non approssima bene. 
Diminuendo banda perdo quindi la definizione del mio sistema 

Le reti LAN usano la trasmissione in banda base

Quando si trasmette ogni tipo di segnale elettrico su una linea di trasmissione, il segnale è attenuato e distorto dal mezzo trasmissivo. Inoltre è sempre presente del rumore.

Problemi: 
- Dobbiamo considerare che sono presenti sempre dei [[Tempi della trasmissione|tempi di trasmissione]]
- Essendo pero due sistemi distribuiti, hanno due clock diversi: è necessario capire quando inizia e quando finisce un bit, saranno quindi necessari algoritmi di sincronizzazione, [[Codifica di Manchester]]
