I tratti biometrici possono essere confrontati per :
- Universalità
- Unicità
- Permanenza
- Collezionabilità
- Performance
- Accettabilità da parte degli utenti
- Facilità di aggiramento (frode)

Ad esempio :
- Il volto ha un alta universalità ma una bassa unicità ( sistemi non ancora abbastanza evoluti per distinguere due volti), facilmente detenzionabile, Bassa permanenza cambia con il tempo.
- Non tutti i tratti vanno bene per fare identificazione e autenticazione nella pratica, nella teoria si :

| Tratto biometrico | Autenticazione | Identificazione |
| ----------------- | -------------- | --------------- |
| Impronta          | SI             | SI              |
| Volto             | Si             | No              |
| Iride             | SI             | SI              |
| Mano              | Si             | No              |
| Voce              | Si             | No              |
| Firma             | Si             | No              |

`Il sistema quando deve effettuare l'identificazione con N troppo grandi potrebbe perdere di performance e accuratezza`.
Ad oggi solo iride e impronta sono stati usati per identificazione ( 1:N) con N grandi.

`Requisiti per il funzionamento 1 : N` :
- `Accuratezza elevatissime` ( tasso errore << 1E-5), l'errore scala con il numero di persone, l'errore sul singolo match deve essere molto basso.
- `Template per byte ridotti` ( dimensione  < kb), altrimenti con N molto grossi dovrei avere una base di dati molto grande dove memorizzarli.
- `Tempo per singolo confronto molto basso` ( t < ms), altrimenti il sistema potrebbe risultare molto lento.
- Altri parametri importanti sono la `durabilità del tratto` biometrico negli anni e il numero massimo di sample indipendenti :

| Tratto biometrico | Variazione negli anni | Numero massimo di sample indipendenti             |
| ----------------- | --------------------- | ------------------------------------------------- |
| Impronta          | no                    | 10 ho 10 dita, sistemi con più dita sono robusti. |
| Volto             | Si                    | 1 ho un volto solo                                |
| Iride             | SI                    | 2                                                 |
| Mano              | Si                    | 2                                                 |
| Voce              | Si                    | 1                                                 |
| Firma             | Si                    | 1 ( se non si associa un parola chiave)           |

[[Variazioni del tratto]]
[[Sample indipendente]]

Fattori da considerare:
- `Costo del sensore`: ha una grande importanza sulla diffusione e l'impiego del sistema.
	Ci possono essere dei sistemi a costo zero (come ad esempio il microfono del cellulare per rilevare il tratto biometrico della voce), oppure dei sistemi biometrici che costano molto (riconoscitore di iride).
- `Dimensione del sensore`: influenza la possibilità di impiego nei vari sistemi elettronici "embedding"
- `Velocità del sistema`
	Tempo di riferimento = è il `tempo misurato in secondi per eseguire completamente un singolo matching`. Da questo tempo si arriva a stimare il numero di utenti massimo identificabile/autenticabile in un ora.
	
	Inoltre i sistemi possono funzionare :
	- in tempo reale: in cui la velocità e cruciale, es gate aeroportuale
	- Off-line: in cui la velocità è importante ma non cruciale, es ricerca delle impronte di un criminale in un archivio
	
	Esempio, Caso dell'aeroporto ( 1 : N ) :
	- Abbiamo 2000 iridi registrate nel sistema come "persone indesiderate" ( N = 2000)
	- Vogliamo che la persona venga identificata negativamente in 2 secondi.
	- Il tempo per eseguire un singolo matching deve essere minore di 1 ms, il qual è davvero poco
- `Interoperabilità`
	Si tratta della `capacità di un sistema biometrico di funzionare anche con sample biometrici acquisiti con sensori di diverso tipo` usando lo stesso tratto biometrico.
	L'argomento della interoperabilità diventerà sempre più importante visto che il tipo di sensori è destinato ad aumentare nel tempo. (esame)
	
	Ad esempio il sistema FBI IAFIS, ovvero un db di template di impronte, viene alimentato con impronte digitale proveniente da vari sensori ( online, inchiostro scannerizzate)
- `Scalabilità`
	Si tratta di `stabilire come viene influenzata l'accuratezza e la velocità del sistema rispetto al numero di campioni contenuti nel sistema`.
	Possono essere generati dei tratti biometrici sintetici per vedere come si comporta il sistema.
- [[Sistemi biometrici - Percezione degli utenti]]
- [[Anello debole della catena di identificazione]]
- [[Sample vs Template]]
- `Problema della proscription`
	Quando un dato biometrico è inviato ad un dato sistema, l'informazione contenuta non dovrebbe  essere usata per altri scopi se non quello dell'uso richiesto dell'utente
	
	`In ogni sistema informativo basato su rete è difficile assicurare che il dato inviato verrà usati per gli scopi richiesti`. Non è solo un problema della biometria, tuttavia quest'ultima prova che la richiesta l'ha fatta un particolare utente (difficile da ripudiare)
	Di conseguenza devono essere stabilite delle politiche di privacy .
- Variazioni del tratto e privacy
	`Usare un tratto biometrico che varia molto nel tempo tende a produrre molti falsi negativi`, il sistema dice che non sono io. Tale errore fa arrabbiare un cliente che ha pagato per il servizio.
	
	Ma allora perche non si utilizzano sempre l'impronta e l'iride visto che hanno tassi di errore tra i più bassi ?
	- Costo del sistema
	- È corretto adattare l'invasività del tratto e l'accettazione degli utenti con il grado di sicurezza richiesto (esame )
	- Usare un tratto che varia nel tempo può proteggere dall'effetto "schedatura"
	
	Un template di una impronta o un iride memorizzato in un sistema biometrico può  provare che un utente è stato in un certo posto per decenni, con errori trascurabili.
	
	Un sistema biometrico basato sulla voce  e legato ad una parola chiave riuscirà ad  identificarvi con elevata accuratezza solo se voi vorrete ripronunciare la parola chiave
	
	Per una centrale nucleare o un aeroporto ha senso usare il primo tipo di biometria, per entrare comodamente a DineyWorld sarebbe meglio usare il secondo tipo