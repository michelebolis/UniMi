Le caratteristiche dei sistemi di riconoscimento degli individui basati su DNA, pongono questa metodologia come `la più accurata nel panorama biometrico`.

Il DNA può essere usato come tratto biometrico con dovute `precauzioni`:
- `Per garantire l'attendibilità del risultato`
- `Per evitare usi impropri delle informazioni` contenute nei sample

Anche se i sistemi basati su DNA vengono utilizzati per valutare le tracce ritrovate su scene del crimine, ad oggi `non esiste un metodo di stima statistica per valutare quanto è affidabile l'associazione fra campioni`:
- Il livello di accuratezza viene ritenuto molto alto dagli esperti
- Viene controllato che vi sia un $profile rarity > 1/10 M$ (a parte gemelli omozigoti)

La produzione di sensori a stato solido per analisi DNA (basati sulla tecnica micro array), fa prevedere nel futuro prossimo una diffusione sempre maggiore dei sistemi biometrici basati su DNA.


Si tratta di una tecnica relativamente giovane 1984. i termini correntemente in uso sono :
- DNA typing (accezione generale)
- DNA profiling o DNA fingerprint

Nel `1986 Mullis` arrivò alla tecnica `PCR` (Polymerase Chain Reaction), si tratta di una tecnica ad oggi automatizzabile che `permette di amplificare un campione di DNA fino ad arrivare ad un comodo template per le operazioni di comparazione`

`Ad ogni ciclo il sistema raddoppia la coppia dei frammenti di DNA`. È critica la quantizzazione del campione iniziale, perché sbagliare il numero di cicli crea un errore molto grande sulla quantità finale di DNA.

La formazione di un individuo ("fenotipo") come la formazione dei suoi `tratti biometrici dipendono dall'interazione del suo patrimonio genetico` (DNA. Genotipo) e l'ambiente.

Il DNA è un `ottimo strumento di identificazione` in biometria per i seguenti motivi :
- Esso è `presente in ogni cellula` del corpo in modo omogeneo
- Un processo di `duplicazione cellulare (mitosi)`, duplica con incredibile precisione la sequenza del DNA
- È una `sequenza assolutamente unica per ogni individuo`:
	- Solo una porzione dal 0.1% al 0.5% è diversa per ogni individuo, il resto è uguale per tutti.
	- Tutta via questa piccola porzione è composta da milioni di basi, ossia elementi costituenti del DNA.
- È `sufficiente un piccolo campione di DNA` per effettuare l'acquisizione del tratto (PCR amplification)

Vantaggi :
- è la `tecnica più accurata a disposizione`.
- Al contrario degli altri tratti biometrici (iride, mano, voce, ecc.) con il DNA `bastano poche cellule`
- Il DNA `permette anche associazioni fra consanguinei` (a differenza degli altri tratti)
Svantaggi :
- Analisi `non real time`, servono minuti/ore
- Procedura non automatizzata
- `Analisi costosa` (100 dollari to 2000 dollari)

[[DNA - Composizione]]

Che feature si estraggano dal DNA:
Si potrebbero estrarre la sequenza di basi che compongono un gene, ma diventerebbe inutilmente complesso.
In alcune regioni del DNA (Loci) vi sono dei `pattern di basi ripetuti, ma ripetuti in un numero di volte diverso in ogni individuo`. Questo tipo di DNA è chiamato `DNA satellite`, le sequenze prendono il nome di `sequenze tandem`.

`La feature biometrica è quindi il numero di ripetizioni in un locus`
Le porzioni di DNA con ripetizioni chiamate satelliti si dividono in :
- `Macro satelliti` (> 100 bp)
- `Mini satelliti` (10-100bp)
- `Micro satelliti` (`2-7bp`) <- biometria attuale DNA

…CTAGTCGT GATA GATA GATA GATTACA… = 3 bp ripetizioni

`STR = short tandem repeat` usate in larga scala in biometria
`SNP = single-nucleotide-polymorphism`  variazione del materiale generico a carico di un unico nucleotide ( G,A,T,C)

![[Pasted image 20240214091723.png]]

Come è costituito un template di DNA:
Il famoso `Combined Dna index system CODIS` FBI database usa per il suo template :
- 13 solo loci in tutti i cromosomi (dal 2017 sono 20)
- Conteggia gli str
Contiene dati su oltre 14 milioni di individui.

Campioni utili per trovare il DNA :
- Sangue
- Sperma
- Saliva
- Urina
- Capelli
- Denti
- Ossa
- Tessuti

È sufficiente una microscopica goccia di sangue o saliva per ottenere un campione valido per un analisi forense. Nelle normali procedure si usa un campione di sangue o un campione di saliva dalla bocca.

Passi nell'`analisi del DNA`:
- `Collezionare il campione di DNA`
- Eseguire una `estrazione del DNA` e una `quantizzazione` (fondamentale per la successiva fase di PCR)
	La porzione di DNA che può essere duplicata è limitata, di conseguenza si procede `solamente alla amplificazione dei loci che ci interessano`. 
	Tutti gli STR che si usano sono estraibili tramite appositi enzimi:
	
	Il DNA è un polimero carico elettro staticamente. Si possono `separare segmenti di DNA di una certa dimensione utilizzando opportuni campi elettrici` (un apposito gel) . Gli alleoli di piccole dimensione sono più veloci nel processo di elettroforesi capillare.
	
	L'amplificazione PCR è estremamente sensibile:
	- Basta un solo capello per completare un analisi
	- Rimane il pericolo della contaminazione, basta solamente un residuo di impronta del tecnico di laboratorio per contaminare il campione.
	- La fase di quantizzazione è fodamentale:
		- `Troppo poco DNA perdo allelei`
		- `Troppo DNA malfunzionamento del kit`
- Il DNA viene duplicato tramite la `PCR amplification`
- `Estrazione e conteggio degli STR`.
- `Matching`.

Fase di PCR e separazione STR:


Una volta separati i vari alleoli avviene il conteggio tramite un apposito sensore laser, che ne esegue la lettura.

Genotipizzazione:
I dati tracciati dal sensore laser, arrivano al software per la `genotipizzazione`, l'esperto `produce e controlla tutti i dati per il template da confrontare e/o memorizzare`.

![[Pasted image 20240214091809.png]]

Problema: esistono moltissimi problemi sperimentali che possono provocare dei `falsi picchi di alleli` o farli scomparire, anche in questo caso si parla di artefatti.
Da questo punto di vista anche il DNA può sbagliare.
`Nei vari loci del CODIS, troviamo due allelei uno proveniente dalla mamma e uno proveniente dal papà`

![[Pasted image 20240214091828.png|300]]

Legame DNA somiglianza face body
`DNA in comune` (gemelli, parenti) -> `Somiglianza biometrica` (face, finger print)
Somiglianza biometrica - > Somiglianza nel DNA

Legame scoperto nel 2022. `Persone estranee ma somiglianti, hanno somiglianza anche genetica, utile per predirre malattie`. Oltre a questo dei sosia possono essere fisicamente simili ma anche caratterialmente.

La fenotipizzazione permette dal sample del DNA di ricostruire il volto?  SNI
`La fenotipizzazione del DNA può aiutare a stabilire come potrebbe apparire l'autore e quindi restringere ulteriormente i sospetti`.  Dopo seguirò la genotipizzazione.

Gli essere umani sono diversi fra loro per il 0,1-0,5% del loro DNA, ma sono ugualmente tantissime basi.

Stanno iniziando a nascere i primi sw, tutta via la sintesi del fenotipio è un operazione che avviene su base statistica.

Gemelli, individui nati durante lo stesso parto, anche se non nello stesso istante. Si dividono in :
- `Eterozigoti` (bi ovulari): 2/3 dei parti gemellari. Derivano dalla fecondazione di due diverse cellule uovo da parte di due spermatozoi diversi, `due fratelli normali con la stessa data di nascita`.
- `Monozigoti`: derivano da una singola cellula uovo fecondata da uno spermatozoo. `Al concepimento hanno lo stesso DNA`.
Solo pochi laboratori capaci di analisi molto avanzate trovano in modulo affidabile le piccolissime differenze del DNA degli omozigoti.  Di conseguenza il CODIS potrebbe non funzionare.


Privacy del DNA
`Autenticazione del DNA parentale`, avviene secondo le seguenti fasi :
- DNA in una banca dati
- Match di un adeguata porzione di DNA dovuta alla parentela
- Ricerca nell'albero genealogico

È stato misurato che in UK mediamente un individuo condivide 175 terzi cugini. Mandando il proprio DNA ad una azienda per l'analisi si possono rintracciare i parenti perché contengono stesse porzioni di DNA.

Il problema è che `espone anche i suoi discendenti e parenti nel futuro`, 1 solo individuo espone > 1000 persone al tracciamento.

Accedendo a un DB di 1.28 M persone si copre il 60% della discendenza europea.

Con il 2% della popolazione schedata con DNA si ha il 90% di accuratezza di risalire senza errori fino al 4 cugino.

Oltre alla possibilità di essere riconosciuto il `DNA fornisce dati su malattie e predisposizioni`, tutte informazioni che se divulgare possono influenzare drasticamente la vita di una persona. 
Tuttavia più di 25 milioni di persone nel 2019 effettuano test sul DNA ad aziende private, le quali espongono il DNA degli utenti.

Nel 2013 il ricercatore Enrich usando dati pubblici ha costruito un albero genealogico di 13 milioni di individui.