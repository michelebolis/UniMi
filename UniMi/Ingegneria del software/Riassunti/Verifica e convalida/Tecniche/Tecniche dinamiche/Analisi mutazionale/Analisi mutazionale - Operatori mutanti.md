Gli `operatori mutanti` sono funzioni che, dato un programma $P$, generano uno o piu mutanti. $\Pi$
I piu semplici effettuano modifiche sintattiche che comportino modifiche semantiche MA non errori sintattici bloccanti in compilazione

Gli operatori si distinguono rispetto all'oggetto su cui operano
- `costanti/variabili`: es scambiando l occorrenza di una con l altra
- `operatori ed espressioni` del programmi: es da < a <= 
- `sui comandi del programma`: es da while in if

Possono essere specifici di alcuni tipi di applicazioni
- Sistemi concorrenti: operano principalmente sulle primitive di sincronizzazione
- Sistemi OO: operano principalmente sulle interfacce dei moduli

I tool moderni lavorano sull'eseguibile in quanto per ogni mutante bisogna modificare il codice, ricompilarlo e controllare

`HOM - High Order Mutation`
Nella variante HOM `si applicano modifiche a codice già modificato`
Esistono infatti casi in cui trovare errori dopo aver applicato piu modifiche è piu difficile