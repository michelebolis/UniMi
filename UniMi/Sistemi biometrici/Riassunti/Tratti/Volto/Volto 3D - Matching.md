Algoritmi di matching 3D
Avendo a disposizione sensori 2D e 3D non è detto che non si possano usare congiuntamente

Schema delle possibilità attualmente possibili :
![[Pasted image 20231115100500.png|400]]
Il confronto fra due volti con tecniche 3D presenta i seguenti passaggi:
- Se il `volto 3D non è direttamente acquisito dal sensore`, allora `da multiple stils si ottiene la rappresentazione 3D dei volti da confrontare` ( tipicamente uno dei volti è già stato memorizzato in fase di enroll)
- `I volti vengono sovrapposti` (rototraslati) fino a trovare la migliore sovrapposizione delle superficie
- `Si valuta il grado di sovrapposizione con una soglia`. Il match prevede l'individuazione di 3 punti di riferimento nelle immagini per facilitare la corretta sovrapposizione.

Per approfondire i risultati ottenibili da queste tecniche ci `dobbiamo riferire solo a prove comparative indipendenti` (dai produttori) sui dati pubblici e non rilasciati prima dei test ( secretati). In ogni caso abbiamo i seguenti risultati:
- FAR (false accept rate) fissato a 0.001 tra tutti i partecipanti. Viene misurato il tasso in verifica. Quante volte il sistema sbaglia nel dire tu sei tu.
- Windows hello face autentication FAR = 0.001% 5% FRR  :
Alcuni aspetti interessati di questo sistema :
- Vengono `utilizzate delle caratteristiche facciali locali`, l'algoritmo prende centinaia di sample da aeree differenti della faccia. `Nessuna immagine della faccia viene memorizzata`. Si tratta di un sistema a feauture locali
- `La rappresentazione deve passare un modello di machine learning prima che l'algoritmo di matching lo identifichi come genuino`. In caso di autenticazione ( con pochi utenti del sistema) la soglia di matching viene alzata.

I passi futuri riguardano la funzione multimodale e l'uso delle reti neurali.


Confronto con umani
Uno degli obbiettivi è quello di arrivare a eguagliare o superare il tasso di riconoscimenti degli umani.
Si è creato il seguente insieme di confronti :
- 240 coppie di facce, 120 maschi e 120 donne 50% facili e 50% difficili
- Diverso colore e lunghezza dei capelli
- Diverse condizioni dello sfondo

Gli umani potevano rispondere con :
- Sono sicuro che siano la stessa persona
- Penso siano la stessa persona
- Not sure
- Penso non siano la stessa persona
- Non sono la stessa persona

3 algoritmi su 7 sono stati capaci di fare meglio dei supervisori umani sul dataset difficile.

Mentre tutti hanno fatto meglio dell'uomo su dataset facili.


Critiche verso il Face recognition
Nel FR si stanno notando grandi miglioramenti in :
- Accuratezza
- Usabilità
- Numero e tipo di dispositivi dove poterlo applicare

Tuttavia l'utenza è preoccupata riguardo alla sua diffusione e alla privacy :
- Molte associazioni di utenti stanno chiedendo di rifiutare l'uso della sorveglianza biometrica negli spazi pubblici
- Alcuni fornitori come ibm, hanno deciso di non fornire più le tecnologie di FR di massa a organi di polizia e municipalità.

Gli errori ( FNMR, FMR, CMC) sono tutta via ancora abbastanza alti da creare un effetto di protezione da "errore del sistema" su schedature a scala metropolitana e nazionali nel FR.
In EU, tutta via, è ancora aperto il dibattito se utilizzare o meno queste tecnologie in screening di massa.


EER  = punto sulla curva det in cui FNMR = FMR
Avevamo indicato fra i principali fattori migliorativi del volto :
- Alta risoluzione delle immagini
- Multi-stil, multiple shots
- Introduzione dei dati 3d
- Artificial intelligence

Controllo del volto 3D usando un sistema 2D.

Partendo dal sensore più semplice, ovvero la camera visibile 2D è possibili eseguire shape from motion.

![[Pasted image 20240214090426.png]]

- `Zoom`: si tratta di una tecnologia che a partire da un immagine frontale del volto, ( la zona centrale è quella del volto che ha maggiori dettagli 3d utili), costruisce un modello 3D.

	Viene realizzato un modello 3D, a partire da camere 2D, tutta via il modello 3D contiene più dati rispetto ad un qualsiasi foto piatta.
	
	Il test di matching viene fatto su immagini 2D.
	- FAR 1/4,200,000 FAR @ less than 1/100 (FRR)
	- 668% better than the top algorithm in lates NIST’s FRVT results. Risultati rilevati mediante test proprietari e non indipendenti.
	- Sempre il produttore afferma che si tratta di una tecnologia molto robusta alle frodi, perfino agli utenti dormienti con occhi chiusi.
	
	Resiste a :
	- Maschere
	- Video ad alta risoluzione
	- Progetti video su teste 3D
	- Impostori, sosia.
- `3D face Map`: si tratta di una tecnologia, la quale partendo da un video di 2 secondi permette di verificare :
	- Vitalità del volto
	- 3D della superficie
	- Riconoscimento del volto 3D.
	Inoltre gode delle seguenti caratteristiche :
	- Interoperabile .= funziona con tutte le camere dei cellulari recenti
	- Controlli di liveness veloci
	- Funziona in condizione ambientali realistiche
	- Funziona anche con occhiali, barba, trucco.