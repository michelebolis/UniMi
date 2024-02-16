I sistemi multi-modali sono dei `sistemi biometrici che utilizzano o sono in grado di utilizzare più di un tratto fisco/comportamentale` per enrollment, identificazione, verifica.
- Monomodale piccola distinzione tra :
	- `Unibiometric`: singola tratto biometrico
	- `Unimodal`: una singola immagine,  una singola rappresentazione, una singolo matcher
- `Multimodale`: sistemi con tratti biometrici scorrelati ( impronta e volto)
- `Multi Biometrico`: cappello generale che comprende sistemi con tratti leggermente correlati, sensori diversi, feature diverse.

L'obiettivo è quello di `aumentare l'accuratezza e la robustezza alle frodi`.
L'essere umano è per sua natura multimodale, riesce a riconoscere contemporaneamente diversi tratti biometrici.

I sistemi multi-modali sono più accurati dei sistemi monomodali che li compongono.
Ad esempio supponiamo di prendere una curva ROC di un sistema che mette assieme i seguenti sistemi mono modali:
- Firma
- Face
- Mano

![[Pasted image 20240214094152.png|300]]

Vantaggi :
- L'accuratezza del sistema viene aumentata, in quanto `utilizzando N tratti biometrici si riesce ad estrarre più informazione, aumentando le performance del matching`
- Riescono a coprire una fascia più ampia di utenti `riducendo il Failure to enroll`, gli utenti che non possono utilizzare un tratto si registrano con un altro
- Più robusti alle frodi, è difficile ingannare più sensori.

Svantaggi :
- Sono `più costosi` essendo composti da più unità biometriche
- Sono `più lenti in acquisizione`.

Come possono essere composti i sistemi:
- Tratti biometrici differenti
- Stesso tratto ma diversi sample
- Stesso tratto ma differenti dita
- Differenti tipi di sensori per lo stesso tratto
- Tipo di feature estratte da un tratto diverse (minutiae e non minutiae matching).

Alcune composizioni sono vicine (iride, volto) per semplicità di acquisizione
Altre composizioni sono assolutamente indipendenti

Possibili applicazioni dei sistemi multimodali:
- Alto
	- Accesso fisico
	- Identificazione (passaporti biometrici)
- Medio
	- Accesso a rete informatica
	- Acesso ad ATM
- Basso
	- Ecormence
	- Telefonia
	- sorveglianza