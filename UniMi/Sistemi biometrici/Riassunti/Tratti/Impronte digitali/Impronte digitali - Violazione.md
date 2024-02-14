Furti d'identità
I furti d'identità costano centinaia di miliardi di dollari all'anno in USA ( principalmente su carte di credito). L'identificazione mediante impronte sembra essere la soluzione più immediata a questo problema.

In realtà come si sono sviluppate le tecniche anti-spoofing, si sono sviluppate anche negli anni le tecniche spoofing, di conseguenza ad oggi esistono molti modi di attaccare un sistema biometrico :
- Attaccare i canali di comunicazione del sistema ( replay attack), specialmente il canale di comunicazione dal sensore al sistema
- Attaccare moduli specifici ( sostituire alcuni moduli con un cavallo di troia)
- Attaccare il DB con tutti i dati di enrollment
- Ingannare il sensore, di solito presentando un sample ad Hoc finto.

La frode di un sistema biometrico non è un evento impossibile e non necessariamente tecnicamente complesso.

Sensor spoofing :
Tassonomia delle tecniche di attacco ad un sistema biometrico basato sulle impronte fornendo ingressi contraffatti (attacco al sensore), esistono due metodi per frodare il sensore :
- Friction ridge falsi
	- Gomma
	- Silicone
	- Gelatina
- Friction ridge veri
	- Amputazioni
	- Trapianti

Analizziamo ora delle frodi che possono essere apportate ad un sistema biometrico :
- FRODE CLASSICA A
	- Supponiamo di avere un utente X, il quale è autorizzato ad entrare nel sistema, esso esegue un enrollment registrandosi con il tratto biometrico L(x)
	- X cede a Y (utente malevolo) il suo tratto biometrico o ne permette una copia. Il tratto l(x) viene ora copiato in A(X), in possesso da Y
	- L'utente Y è ora in grado di essere autenticato dal sistema, l'utente malevolo Y è riuscito ad entrare nel sistema.
	- Il tratto A(X) può essere ceduto o copiato e ceduto a più utenti malevoli.
-  FRODE CLASSICA B
	- X ottiene A(Y) tratto biometrico di un utente malevolo Y
	- X dato che ha i permessi per effettuare l'enrollment, registra nel sistema il tratto biometrico A(Y) associandolo a se stesso.
	- Ora Y è in grado di essere identificato/autenticato dal sistema
	- Il tratto A(Y) può essere distribuito a più utenti malevoli
- FRODE CON tratto casuale
	- X viene in possesso del tratto biometrico A(Y) , A(Y) è un tratto biometrico casuale.
	- X registra nel sistema tramite uan fase di enrollemet il tratto A(Y), associandolo a se stesso
	- X è in grado ora di essere autenticato/registrato dal sistema
	- Il tratto A(Y) può essere ceduto o copiato ad altri utenti malevoli.
- Tentativi di frode anomali
	- Amputazioni di dita per rubare automobili di lusso dotate di accensione a chiave biometrica ( frode riuscita)
	- Trapianti delle dita dei piedi su quelle della mano per frodare il programma US-VIST americano ( frode fallita)

Attacchi al sensore
È possibile ingannare un sensore di riconoscimento dell'impronta digitale tramite un dito finto ? La risposta è si e in vari modi
- FAKE fingers
È possibile ricreare la superficie dell'impronta con vari materiali, la superficie dell'impronta può essere ricreata a partire da :
- Un impronta "lifted" presa da una scena (ad esempio un bicchiere in un bar)
- Da un immagine rubata da un sistema
- Da un dito reale di una talpa

Vediamo ora i risultati che ottiene la clonatura di un impronta di un dito vero  :
La tecnica  utilizzata maggiormente è quella ideata da Matsumoto, permette di duplicare un impronta su un dito reale . Risulta molto semplice, poco costosa ( semplici materiali, plastica, gelatina) e inoltre da buoni risultati.
![[Pasted image 20231106110405.png]]
Nella pratica cosa succede se diamo impasto un impronta finta a vari tipi di sensore ?
- I sensori ottici, non riescono a distinguere le impronte vere da quelle false  
- I sensori capacitivi non riescono a distinguere le dita realizzare in gelatina da quelle vere, tutta via si proteggono dalle dita in silicone.

Risultati del prof Matzumoto :
- Il professore è andato a testare le impronte finte su 11 sistemi commerciali più diffusi sul mercato.
- Il test prevedeva 4 condizioni

| Enroll           | Verification     |
| ---------------- | ---------------- |
| Dito vero        | Dito di gelatina |
| Dito vero        | Dito di gomma    |
| Dito di gomma    | Dito di gelatina |
| Dito di gelatina | Dito vero        |

- Il test venne ripetuto 100 volte, circa 4 volte su 5 i sitemi biometrici sono stati ingannati dal dito artificiale
- Altri test indicano percentuali di spoofing vicine al 90%

È possibile tramite altre tecniche copiare anche le impronte latenti.

- Attacco del nastro
Questa tecnica di spoofing è molto semplice da realizzare :
- Il signor X entra in un ambiante protetto con un sistema biometrico appoggiando la sua impronta sul sensore.
- Il signor Y (impostore) passa subito dopo e soleva l'impronta fresca con un nastro apposito.
- Il signor y evidenzia l'impronta ( povere per impronte), la fotografa ed inizia il procedimento di duplicazione per le impronte latenti
È importante non lasciare il tratto biometrico sul sensore.


Generazione sintetica di impronte
Sono disponibili in letteratura dei generatori di impronte sintetiche che, partendo da numero casuali, sono in grado di generare immagini di impronte perfettamente verosimili.
Questi generatori casuali permettono di simulare delle condizioni ambientali a piacere, ad esempio :
- Sfondi
- Rumore di acquisizione
- Dimensione e forma dell'impronta

I generatori generano un sample di un impronta partendo al contrario, si parte dai punti singolari, si calcola il loro orientamento e infine si aggiungono i ridge e il rumore.

Di solito tali generatori vengono utilizzati per testare dei sistemi biometrici nuovi, senza dover ricorrere a costose campagne di acquisizione mediante volontari. Tutta via tali prove con impronte sintetiche non potranno mai sostituire i test con impronte vere.


Tecniche antispoofing
Anti-Spoofing hardware o software :
- SW
	- Valutando le caratteristiche del campione (nitidezza del rughe e presenza di pori).
	- Il software ha il vantaggio si essere facilmente implementabile e facilmente aggiornabile.
	- Permette di implementare di modelli di machine -learning o di deep learning atti a fare anti-spoofing.
- HW
	- Richiede funzionalità aggiuntive nello scanner di impronte digitali, come il capacità di rilevare impulsi, temperatura e capacità, nessuno dei quali può essere fatto solo nel software
	- L'hardware ha il vantaggio di avere una migliore accuratezza nel rilevare la vitalità di un impronta
	- Più dispendioso, consuma maggiore potenza, introduce latenza.
	
 - Test di vitalità per sensori ottici
Uno degli approcci più comuni al test di vitalità consiste nell'usare uno o più segnali vitali comuni a tutta la popolazione di riferimento :
- Il flusso sanguigno e la sua pulsazione possono essere rilevati mediante luce riflessa o trasmessa attraverso il dito
- La temperatura e la sua distribuzione può indicare se il dito è vivo, morto o fasullo

Gli scanner ottici di tipo live-scan con le tecnologie FTIR ( frustated total internal reflection) o i sensori allo stato solido utilizzano un meccanismo di acquisizione differenziati per le creste ed i solchi delle impronte digitali :
- Resistono agli attacchi portati con immagini 2D fasulle.

I sensori ad alti risoluzione ( > 700 DPI) rilevano i dettagli del 3 livello ( pori, incipient ridges) difficile da imitare in un dito artificiale ( per adesso)

La pelle del dito cambia colore per effetto della pressione, quando esso viene premuto sul sensore di scansione, questo effetto può essere rilevato.

I test di vitalità iniziano solo oggi a diffondersi, molti sitemi commerciali biometrici basati su sensore ottici possono essere frodati con dita di silicone e gelatina


- Test di vitalità per sensori allo stato solido
	- La differenza di potenziale tra due specifici punti della muscolatura del dito ( miografia) può essere utilizzata per distinguerlo con un dito morto.
	- La misurazione dell'impedenza del dito può essere utile per verificare la vitalità del dito
	- La sudorazione continua di un dito e la sua evoluzione temporale sul sensore è un ottimo test di vitalità

- Altri testi di vitalità ( non ancora disponibili ma in fase di sperimentazione)
	- Analisi della deformazione meccanica del dito durante l'acquisione, che distingue il dito vivo da quello falso fatto con gelatine, siliconi, o gomme
	- Nasi artificiali per la rilevazione di odori e sostanze che non sono presenti sulle dita vive ( solventi, gomma)
- Per ridurre gli attacchi sulle comunicazione, possono essere apportare le seguenti tecniche
	- Synaptics: può essere utilizzato il protocollo TLS ( transport Layer Security), per crittare la comunicazione tra il sensore e l'host ricevente.
	- Match in sensor tecnology: ogni scansione di un impronta viene interamente autenticata sul sensore. Il quale inoltre contiene in modo sicuro l'impronta dell'utente usata nelal fase enrolment.