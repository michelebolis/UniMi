Prima di parlare sei sensori in commercio, andiamo a stabilire quale luce è meglio per acquisire l'iride :
- `Luce visibile`
	- `Si vedono gli strati` che compongono l'iride
	- `Si vede meno la tessitura` (più interessante per il sistema biometrico)
	- La melanina dei pigmenti assorbe la luce visibile ( quindi se non irradia non la vediamo)
	- Inoltre con la luce visibili abbiamo una `maggiore variabilità intraclasse`, rendendo il problema del riconoscimento ancora più complesso
	- Gli occhi scuri sono più problematici e offrono meno dettagli utili al riconoscimento
	- La fonte di luce utilizzata `non può essere troppo intensa`, altrimenti darebbe fastidio all'utente.
- `Luce infrarossa` (IR)
	- `La melanina riflette molto meglio la luce IR`
	- Si vedono meglio i pattern casuali e distintivi tipici dell'iride

`Le feature maggiormente interessanti per il sistema biometrico si vedono meglio con la luce IR` piuttosto che con la luce visibile.

Per catturare i complessi dettagli dell'iride, il sistema di acquisizione deve poter risolvere con `almeno 70 px il raggio dell'iride ( di solito 100-140 px)`.
Si usano CDD monocromatici (almeno $640*480$ ) capaci di acquisire ad infrarossi.

`L'illuminazione migliore per rilevare i dettagli deve cadere nella banda di 700-900 nm` ( non visibile all'occhio), è quindi necessario utilizzare telecamere con ottiche variabili per trovare l'occhio nel volto e poi zoomare verso l'occhio per acquisirlo alla massima risoluzione possibile: in alcuni casi si usano 2 telecamere con due ottiche diverse al posto di uno zoom.

Esempi di sistemi
Una delle più grandi applicazioni dei sistemi biometrici basati sull'iride è il sistema nazionale delle frontiere degli emirati arabi :
- 17 aeroporti e tutti i porti di mare
- 3.8 milioni di comparazioni eseguite ogni giorno
- Un singolo match eseguito in una frazione di secondo

Altri esempi di applicazione di riconoscimento dell'iride :
- Computer login ( l'iride è una password vivente)
- Frontiere nazionali (l'iride è un passaporto vivente)
- Accesso sicuro ad ATM
- Autenticazioni per le carte di credito
- Anti terrorismo

Esempio di ATM :
- Il gruppo bancario americano Citgroup, usa un ATM con riconoscimento dell'iride
- Si prevede un tempo per prelevare del denaro da 45 secondo a 15 secondi
- Anche in una versione senza schermo e tastiera che usa lo smart phone del cliente per I/0