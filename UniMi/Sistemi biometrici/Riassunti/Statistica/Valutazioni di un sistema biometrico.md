Possibili valutazioni di un sistema biometrico :
Un sistema biometrico può essere valutato sotto diversi aspetti :
- [[Tecnology Evaluation]]: si tratta di `valutazione offline`, vengono effettuate utilizzando più algoritmi per la stessa modalità biometrica.
- [[Scenario evaluation]]: valutazioni in cui le `prestazioni del sistema sono valutate in un prototipo o in un applicazione simulata`.
- [[Operational Evaluation]]: valutazione un cui l'intera valutazione del sistema biometrico viene determinata `in un specifico ambiente applicativo, con un specifico target di utenti`.

Ogni valutazione ha le sue regole da seguire ed i suoi parametri da misurare.

Online Evaluation vs Offline Evaluation:
- `Online Evaluation`: si tratta di tipi di sistemi che `pretendono di eseguire l'enrollment o il matching al momento dell'acquisizione del sample da parte del sensore`.
	- Il vantaggio principale è che `il sample può essere immediatamente scartato`. Tutta via è consigliabile che l'immagine o il segnale siano collezionabili.
	Con valutazioni su `scenari e test operativi`, le transazioni online potrebbe essere più semplici per il tester (il sistema funziona al suo solito modo) e, anche se consigliato, l'archiviazione di immagini o segnali non è assolutamente necessario
- `Offline Evaluation`: `l'esecuzione dell'enrollment o del matching avviene in un momento separato rispetto all'acquisizione dell'immagine da parte del sensore`:
	- Vengono collezionate una serie di immagini per l'enrollment offline e il matching offline. Questa caratteristica `permette di avere un gran controllo su quali tentativi e template devono essere utilizzati in ogni transizione`
		Ad esempio è possibile sistemare il quality check module
	- I test di tipo tecnologico portano a salvarsi i sample in ingresso per delle computazioni offline.

N.B i tassi di errore non significano nulla se non è possibile associarli un tasso di confidenza ad ogni misura. Gli `intervalli di confidenza` vengono costruiti di solito non da esperimenti, ma da un modello statistico che deve descrivere meglio possibile l'esperimento.