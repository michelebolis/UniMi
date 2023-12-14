Obiettivo: da www.unimi.it vogliamo avere 159.149.141.141:80
Vengono fatte delle query SQL mandando dei messaggi con il protocollo DNS
- Lato host: il browser chiede a un resolver di tradurre le stringhe in numeri attraverso il SO. Viene fatta una cache temporanea per memorizzare i risultati delle query DNS fatte precedentemente
- Local name server: ha un servizio aperto sulla porta 53 che utilizza UDP. Il resolver manda un query DNS al local name server (al primario, secondario per ridondanza). 
	- SE la risposta è nota al local name server viene mandata una response DNS con il record corrispondente (includendo un TTL). 
	- SE la risposta non è nota, utilizza una porta X utilizzando UDP per richiedere la stessa traduzione ad altri DNS


Risoluzione
1. Host host.di.uni.it manda una DNS query chiedendo www.google.com al local name server all indirizzo ns.di.unimi.it (per configurazione). Si opera iterativamente, cercando la risorsa partendo dal dominio piu esterno (ITERATIVO = RICORSIVO)
2. mando a root una DNS query chiedendo www.google.com. La root non conoscendo tale nome, risponde con l indirizzo IP del domain name server di .com
3. mando a .com una DNS query chiedendo www.google.com. Il domain name server .com non riesce a risolvere, quindi manda l'indirizzo IP di google.com
4. mando a google.com una DNS query chiedendo www.google.com e stavolta risponde con un record A con l IP 

Invece di contattare la root avremmo potuto chiedere a un DNS piu vicino, cioè a .com