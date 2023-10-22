Vogliamo trasmettere dei bit sul canale.
Facciamo variare un livello di voltaggio, -V per lo 0 e +V per l 1
Modulatore: modula un onda sinusoidale per darle una forma approssimata, a banda limitata cioe un certo numero di armoniche (ognuna una frequenza in Hz). 
Se uso poca banda (poche armoniche), la forma del segnale non approssima bene. 
Diminuendo banda perdo quindi la definizione del mio sistema 

In una comunicazione vi è sempre un rumore elettromagnetico che disturba la comunicazione, ma il ricevitore non puo riconoscere quale punto sia dato dal segnale iniziale e quale dal rumore. Alcuni bit potrebbero invertirsi

Anche il livello 1 è composto da due livelli funzionali
- Livello Convergence: funzionalità di rete quali la trasmissioni dati, enable/disable della trasmissione, CS, collision detection (fisicamente queste funzionalità li fa il transiver, ma l'informazione deve essere passata al MAC)
- Livello physical medium-dependent : dipende fortemente dal mezzo che sto utilizzando


[[Cavi fisici]]