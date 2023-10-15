è una tecnica di progettazione che guida verso il design piu semplice: Red-Green-Refactor
Nonostante ci sia scritto Test, in realtà è un attività di design
Preparando il test, sto scrivendo una specifica, ciò che deve fare il codice, e mi sto mettendo nei panni dell'utilizzatore del metodo.
Passi:
- Scrivi un test che fallisce
- Qual è la piu rapida ottimizzazione che mi permetta di ottenere il Green? Ottengo un test che passa
- Refactor, attività di design pura
TDD = test-first + baby steps

Partire con un test è in realtà pericoloso perché ci si basa unicamente su di esso in quanto non sappiamo se sia un rappresentante abbastanza generico

L'obiettivo è avere il prima possibile un feedback rapido: ripeto il TDD ogni 2-10 minuti