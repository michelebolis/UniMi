Occupiamoci ora di migliorare la fase di Rappresentazione
- Rappresentazione del sample
- Estrazione delle caratteristiche
- Del template

`Rappresentazione`: una `acquisizione di un sistema biometrico` ( non elaborata) è tipicamente :
- `Non invariante` (rispetto al momento di acquisizione), il sistema deve trovare la parte del tratto che non varia nel tempo e salvarsi quelle informazioni.
- Ed è decisamente `non discriminatoria` (sono tutte diverse), le informazioni estratte devono essere univoche.

In un sistema biometrico occorre studiare come meglio rappresentare l'informazione per rispondere alla domanda:
"`quale rappresentazione "machine-readable cattura completamente l'informazione invariante e discriminatoria della misura in ingresso`"

Il problema della rappresentazione, consiste nel `determinare uno spazio di misura` (feature space) che sia :
- `Invariante` (meno variante) `rispetto ad acquisizioni dello stesso individuo`
- Che `si differenzi massimamente per le acquisizioni provenienti da individui diversi`.
In altre parole si può affermare che la rappresentazione deve fornire una :
- `Alta variabilità interclasse`
- `Bassa variabilità intra-classe`

![[Pasted image 20231106094844.png|300]]
(esame)

La fase di rappresentazione è uno dei cardini della progettazione di un sistema biometrico, `influenza direttamente tutte le fasi successive della progettazione`.
Le problematiche inerenti al problema della rappresentazione nel sistema biometrico per la parte di estrazione delle caratteristiche e della creazione del template impattano sul modulo evidenziato (feature extration) `presente sia in fase di enrollment che di verification/identification`

`L'affidabilità della rappresentazione dipende dal`:
- `Tratto biometrico`: tratti biometrici "semplici" ( basso contenuto informativo, come la firma) produrranno rappresentazioni meno affidabili dei tratti "complessi" come ad esempio la firma.
- `Dominio applicativo del sistema`: la rappresentazione diventa meno affidabile se :
	- All'aumentare degli individui da confrontare fra loro ( aumento dei record del db). Diminuisce la varianza inter-classe
	- In caso di sensori rumorosi, soggetti non collaborativi.

`Rappresentazione del sample`: si riferisce alla `caratteristiche tecniche del processo di acquisizione e memorizzazione` ( anche temporanea) del sample, le quali vanno a generare il template. 
Ovviamente tali tecniche di memorizzazione variano a seconda del tipo di tratto biometrico :
- Firma online = intervallo di campionamento, numero di bit del dato, numero degli assi rillevate
- Impronta digitale = metodo di acquisizione, risoluzione del dispositivo, numero di bit dei toni di grigio.

Spesso si riferisci a questi dati con `RAW data`

`Una volta ottenuti i dati raw, provenienti dalle misurazioni (sample) occorre ora estrarne la rappresentazione nello spazio delle caratteristiche`.
Esistono sia sistemi manuali che automatici per l'estrazione delle caratteristiche.
I sistemi completamente automatici non seguono quasi mai un approccio simile, lo spazio delle caratteristiche di un sistema automatico tende ad essere diverso da quello di un sistema manuale. Inoltre ha una struttura organizzata in moduli software.

![[Pasted image 20231106094936.png]]

Questo non è mai un problema semplice specialmente con dati rumorosi.