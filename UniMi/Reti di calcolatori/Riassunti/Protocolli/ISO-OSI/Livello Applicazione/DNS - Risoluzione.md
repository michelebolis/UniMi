Obiettivo: da www.unimi.it vogliamo avere 159.149.141.141:80
Vengono fatte delle query mandando dei messaggi con il protocollo DNS
- Lato host: il browser chiede a un `Resolver` di tradurre le stringhe in numeri attraverso il SO. Il resolver è in grado di fare delle DNS query al server primario o secondario (i cui IP sono noti al resolver). Viene fatta una cache temporanea per memorizzare i risultati delle query DNS fatte precedentemente. 
- Local name server: ha un servizio aperto sulla porta 53 che utilizza UDP. 
	- SE la traduzione è nota al local name server viene mandata una response DNS con il record corrispondente. 
	- SE la traduzione non è nota, utilizza una porta X con UDP per richiedere la stessa traduzione ad altri DNS


Risoluzione iterativa
1. Host host.di.uni.it manda una DNS query chiedendo www.google.com al local name server all indirizzo ns.di.unimi.it (per configurazione). Si opera iterativamente, cercando la risorsa partendo dal dominio piu esterno 
2. mando a root una DNS query chiedendo www.google.com. La root non conoscendo tale nome, risponde con l indirizzo IP del domain name server di .com
3. mando a .com una DNS query chiedendo www.google.com. Il domain name server .com non riesce a risolvere, quindi manda l'indirizzo IP di google.com
4. mando a google.com una DNS query chiedendo www.google.com e stavolta risponde con un record A con l IP 

Risoluzione ricorsiva 
Quando un local name server non contiene l'IP per il domain name richiesto, richiede lui stesso ricorsivamente tale informazione con una DNS query in modo gerarchico (root -> country -> ...)