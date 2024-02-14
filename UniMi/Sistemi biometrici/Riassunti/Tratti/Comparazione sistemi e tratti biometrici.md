Comparazione sistemi e tratti biometrici
È un problema molto complesso per i seguenti motivi :
- Vi sono molti parametri in giudizio
- I parametri sono difficilmente stimabili, alcuni esempi di parametri :
	- Gradimento degli utenti := parametro importante, misurabile tramite questionari ( domanda di esame)
	- Velocità := numero di confronti che viene eseguito tra il template da verificare e una serie di campioni ( data set).
	- Accuratezza = percentuale con la quale un sistema identifica un utente in maniera corretta.
	- Scalabilità := numero di persone per le quali il sensore è progettato potrebbe aumentare.
	- Interoperabilità := il sistema dovrebbe poter utilizzare diversi tipi di sensori
	- Costo del sistema
	- Usabilità

I tratti biometrici possono essere confrontati per :
- Universalità
- Unicità
- Permanenza
- Collezionabilità
- Performance
- Accettabilità da parte degli utenti
- Facilità di aggiramento ( frode)

Ad esempio :
- Il volto ha un alta universalità ma una bassa unicità ( sistemi non ancora abbastanza evoluti per distinguere due volti), facilmente detezionabile, Bassa permanenza cambia con il tempo.
- Non tutti i tratti vanno bene per fare identificazione e autenticazione nella pratica, nella teoria si :

| Tratto biometrico | Autenticazione | Identificazione |
| ----------------- | -------------- | --------------- |
| Impronta          | SI             | SI              |
| Volto             | Si             | No              |
| Iride             | SI             | SI              |
| Mano              | Si             | No              |
| Voce              | Si             | No              |
| Firma             | Si             | No              |

Il sistema quando deve effettuare l'identificazione con N troppo grandi potrebbe perdere di performance e accuratezza.
Ad oggi solo iride e impronta sono stati usati per identificazione ( 1:N) con N grandi.

Requisiti per il funzionamento 1 : N :
- Accuratezza elevatissime ( tasso errore << 1E-5), l'errore scala con il numero di persone, l'errore sul singolo match deve essere molto basso.
- Template per byte ridotti ( dimensione  < kb), altrimenti con N molto grossi dovrei avere uan base di dati molto grande dove memorizzarli.
- Tempo per singolo confronto molto basso ( t < ms), altrimenti il sistema potrebbe risultare molto lento.

Volto, Mano, Voce e firma vengono solo usati per :
- Autenticazione ( 1:1)
- Identificazione (1;n ) con N molto piccoli

- Altri parametri importanti sono la durabilità del tratto biometrico negli anni e il numero massimo di sample indipendenti :

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