Texture Based Matching FilterBanks
Questa tecnica estrae delle informazioni locali da N regioni dell'immagine. 
Usando un `banco di filtri Gabor` di M filtri, estrae M coefficienti/immagini filtrate per ciascuna delle N regioni elaborate. L'algoritmo di matching compara N * M elementi fra le due immagini.

Vantaggi:
- Ha delle `buone performance anche con delle impronte di scarsa qualità`
- Usa delle informazioni riguardanti la texture dell'impronta per il matching (non utilizzate negli algoritmi minutae o optical base)
- Le features sono `statisticamente indipendenti dalla minutae` e possono essere combinate con le minutae per avere un accuratezza più alta
- Le immagini possono essere normalizzate tramite delle tecniche molto semplici

Svantaggi:
- `Richiede un ottimo allineamento delle impronte da confrontare`
- Può essere `soggetto agli effetti collaterali` causati dalle rotazioni e traslazioni
- `Meno accurato degli algoritmi minutae based`