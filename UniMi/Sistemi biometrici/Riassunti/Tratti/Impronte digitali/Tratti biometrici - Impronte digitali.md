Introduzione
Si tratta di uno dei tratti biometrici più diffusi e più antichi del mondo.

Ad oggi `si ritiene che siano uniche` (non sono mai state trovate due persone diverse la cui impronta possa essere scambiata) e che `non cambino nel tempo`, la disposizione resta la stessa.

Soddisfa dunque le proprietà di un tratto biometrico.

Identificare se un impronta è la stessa rispetto ad una già registrata è un problema di pattern matching molto complesso.
Si utilizzano vari tipi di sensori per identificare un individuo tramite la sua impronta.

È inoltre molto difficile progettare sistemi che riescano a :
- Funzionare anche con diverse condizioni della pelle (sudore)
- Funzionare anche con piccoli overlap (interruzioni nell'impronta), sovrapporre due impronte potrebbe risultare difficile.
- Aumentare la qualità del sample rilevato, qualità dei tratti diverse.

[[Impronte digitali - Storia]]

Come sono Composte le impronte digitali
Le impronte digitali sono `creste e valli della pelle` sui palmi e sulle dita di molti animali.
Si tratta di tratti biometrici stabili fin dall'ottavo mese di gestazione ( a meno di malattie o gravi incidenti).
Esiste inoltre una `parziale simmetria della classificazione fra le dita della mano sinistra e  destra`.

Le varie "valli" che troviamo su un impronta digitale prendono il nome di `Ridges`:
- Sono senza peli
- Contengono moltissimi pori sudoripari
- Non contengono glandi sebacei
- Molte connessioni nervose
- Non si pigmenta

Il `sistema di classificazione` attuale, utilizza 3 categorie. Le impronte si dividono in :
- `ARCH` (Plain e Tented) :
`Plain`: i `ridge entrano da un lato del sample e fluiscono dall'altro lato` del sample, con una specie di onda al centro dell'impronta.
`Tented` : come prima ma i `ridge al centro dell'impronta tendono a formare una specie di triangolo`.  (un core e un delta)
- `LOOP` (left, right)
	Essentials of a loop:
	- Sufficient recurve;
	- Un solo delta
	- A ridge count across a looping ridge.
- `WHORL` ( Plain, twin loop, Accidental, Central Pocket)
The type of pattern in which
- at least two deltas are present
- with a recurve in front of each
- Accidental: a volte categorizzata come Whorl, combina due tipi diversi di pattern o nessuno

Ognuna delle 3 categorie si divide a sua volta in due sotto-categorie (tranne Whorl), per un totale di 3 categorie e 8 sotto-categorie.
Le classi inoltre non sono distribuite uniformemente. Ad esempio ARCHES è quella contenente meno impronte, mentre loop è la categoria più diffusa.

I sistemi di classificazione `attribuiscono una certa categoria ad un impronta` in base a :
- L'individuazione degli eventuali core (punti di unione) e delta (punti di biforcazione)
- Lo studio degli orientamenti dei ridge.
![[Pasted image 20231106101829.png]]
Le impronte digitali, possono essere applicate nei seguenti contesti :

| Applicazioni forensi                                           | Governative                                                            | Commerciali                                                                      |
| -------------------------------------------------------------- | ---------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Identificazione di :  Corpi  <br>delle persone  <br>terroristi | Carte d'identità  <br>Controllo degli accessi  <br>Controllo documenti | ATM  <br>Accesso a servizi online  <br>Telefoni cellulari  <br>Controllo accessi |

[[Impronte digitali - Sistemi AFIS]]
La sentenza 2559 del 14.11.1959 espressa dalla Corte di Cassazione indica in 16 17 punti caratteristici il minimo numero di segni uguali per forma, posizione ed orientamento


Tecnologie concorrenti sul mercato :
- Sistema della ditta M2SYS :
Si tratta di un sistema multimodale `ABIS Automatic Biometric Identification System`
Si tratta di un architettura che supporta il matching biometrico sia in identificazione ( 1;N) che in verifica (1:1), il sistema può cercare un match in oltre 200 milioni di irdi o 100 milioni di impronte al secondo
- Sistema della dita dermalog
Come prima si tratta di un sistema multimodale.
È il sistema di riconoscimento biometrico più veloce al mondo, è in grado di cercare un matching con 129 milioni di impronte al secondo
- Tecnologia SDK
Alte prestazioni e tanta integrabilità
Permette di effettuare dei match on card, supporta sia PC, mobile che sistemi embedded.
Abbiamo un accuratezza del 99.98% ed è in grado di eseguire 1 milione di matching al secondo.

[[Impronte digitali - Rappresentazione]]
[[Impronte digitali - Unicità]]

Nel modulo di estrazione delle feature si eseguono tipicamente i seguenti passi :
- [[Impronte digitali - Filtraggio iniziale]]
- [[Impronte digitali - Manipolazione immagine, Enhancement]]
- [[Impronte digitali - Estrazione delle feature di un impronta]]
- Codifica 

[[Impronte digitali - Matching di due impronte digitali]]
[[Impronte digitali - Violazione]]
