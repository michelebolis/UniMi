Fissato un valore centrale, mi posso chiedere se le mie osservazioni sono vicine o lontane. 
- [[Indici di dispersione - Scarto assoluto medio]]
- [[Indici di dispersione - Varianza campionaria]]
- [[Indici di dispersione - Percentile campionario]]
- Coefficiente di variazione
$$s^*=\frac{s}{|\overline x|}$$
Ci permette di confrontare la variabilità tra due campioni ma hanno valori molto alti, dividendo s, che è influenzata da tali valori, per la media riesco a bilanciare s

Varie graduazioni
- Decile
- Quartile
	Il 25-esimo percentile campionario si chiama primo quartile.
	Il 50-esimo percentile campionario si chiama mediana o secondo quartile.
	Il 75-esimo percentile campionario si chiama terzo quartile.
- Quantili: Se uso numeri reali, avrò p infiniti sui reali

Come calcolare gli indici di dispersione su una serie
- .var restituisce la varianza campionaria
- .std restituisce la deviazione standard campionaria
- .describe calcola i principali indici descrittivi di centralità e dispersione
- .quantile(.quantile) restituisce il valore del quantile specificato