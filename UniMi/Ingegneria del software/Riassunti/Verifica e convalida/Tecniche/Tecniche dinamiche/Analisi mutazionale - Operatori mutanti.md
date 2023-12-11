Sono funzioni che, dato P, generano uno o piu mutanti
I piu semplici effettuano modifiche sintattiche che comportino modifiche semantiche MA non errori sintattici bloccanti in compilazione

HOM High Order Mutation

Gli operatori si distinguono rispetto all'oggetto su cui operano
- costanti/variabili: es scambiando l occorrenza di una con l altra
- operatori ed espressioni del programmi: es da < a <= 
- sui comandi del programma: es da while in if

Possono essere specifici di alcuni tipi di applicazioni
- Sistemi concorrenti: operano principalmente sulle primitive di sincronizzazione
- Sistemi OO: operano principalmente sulle interfacce dei moduli

OSS Un caso di test NON da origine ad una esecuzione MA ad n+1 dove n è il numero di mutanti
E' possibile mediante un'opportuna infrastruttura, automatizzare la generazione, esecuzione e controllo