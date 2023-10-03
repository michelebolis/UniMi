Essedo la memoria di Arduino (e in generale dei dispositivi embedded) ==molto limitata==  (intorno ai 2 KB) è bene gestire con cura le tipologie di variabili dichiarate.
es: se necessito di un numero che va da 1 a 10 è inutile dichiarare una variabile di tipo long(4B) e neanche un int(2B), ma basterebbe un byte(1B # da 0 a 255) o un char(1B)

Dato che anche i record di attivazione delle chiamate di funzioni occupano stack, è utile cercare di ridurle evistando lo stack overflow.

Se si usano diverse stringhe preformate si può ridurre l'uso della RAM usando la funzione F() per leggere direttamente dalla Flash le stringhe.

Anziché scrivere;

 ```c
 Serial.print("Stringa");
 ```

Si scriverà:

 ```c
 Serial.print(F("Stringa"))
 ```

Ciò vale per qualsiasi stringa predefinita.
La stringa verrà presa direttamente dalla flash quando necessaria anziché ricopiarla prima in RAM.

Legato all'uso di memoria è anche la [[Sistemi embedded/Device/Arduino/Ricorsione]]

In ambito embedded, solitamente vengono utilizzate memorie NAND per lo storage principale e le NOR per le funzioni di basso livello e il boot.

Per ==**XIP**== si intende "execution in place", che è una caratteristica fondamentale delle porte NOR nei processori che le supportano; sostanzialmente non c'è il bisogno di caricare il codice oggetto contenuto sulle porte NOR su un'eventuale memoria esterna.  
Il pregio principale è rappresentato dal fatto che è ideale nelle fasi di "boot" in cui la memoria di sistema potrebbe non essere ancora accessibile.