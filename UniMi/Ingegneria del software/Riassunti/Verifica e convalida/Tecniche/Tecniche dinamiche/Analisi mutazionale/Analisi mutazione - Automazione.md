OSS Un caso di test NON da origine ad 1 esecuzione MA ad n+1 dove n è il numero di mutanti
E' possibile mediante un'opportuna infrastruttura, automatizzare la generazione, esecuzione e controllo

![[Pasted image 20231211103116.png|400]]

Questo algoritmo non garantisce la terminazione in quanto
- quando si estrae un caso di test si potrebbe estrarre sempre lo stesso
- non si potrebbe trovare un caso di test utile in tempo breve
- esistono infinite varianti di programmi funzionalmente identici ma sintatticamente diversi

Viene quindi solitamente imposto un timeout dipendente sia dal tempo totale di esecuzione sia dal numero di casi di test estratti