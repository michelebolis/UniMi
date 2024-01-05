Oggi non è di interesse quale server eroga il servizio, ma ricevere il servizio stesso

Obiettivo: migliorare le prestazioni di consegna del contenuto
Problema: i contenuti hanno diversa "popolarità"

George Zipf 1949 ha analizzata la frequenza delle parole in un testo
Stessa distribuzione per i contenuti web
Se consideriamo la distribuzione logaritmica, ne esce una linea retta decrescente
Un 20% del contenuto occupa l 80% del traffico

La rete Internet ha sviluppato due modalita per gestire i due tipi di contenuti
Le CDN si concentrano sui contenuti popolari, considerando anche la variabilita della popolarita anche circoscritta in una certa area geografica
La variazione di popolarita puo essere data dalla viralita del contenuto
Vincolo permanente è quello del posizionamento geografico ($t_P$) che causano perdita prestazionale

Prima delle CDN sono necessarie infrastrutture per gestire una mole elevata di contenuti: Server farm
C'è un server che bilancia il carico tra i vari server (scalabilità orizzontale e elasticità nel fornire un servizio (SE il servizio ha poche richieste, viene fornita una sola macchina MA se diventa popolare, allora viene replicato il servizio su piu istanze))

Data una richiesta di contenuto, come faccio a indicare diversi server? Uso DNS in modo che risponda con diversi indirizzi IP
Alternativa è usare un approccio front end nascondendo gli indirizzi IP dei vari server. Una volta ricevuta la richiesta o faccio round robin o invio a tutti i server la richiesta e ogni server decidera se prendere in carico tale richiesta

Il servizio viene erogato in modo diverso in base alla posizione rilevata della sorgente
Modalita
- Anycast: permette ai router di annunciare lo stesso indirizzo IP da punti diversi. 
- DNS: diversi DNS risponderanno con diversi IP.
- Diversi URL per recuperare risorse 

Fasi meccanismo basato su DNS
1. Fase di distribuzione dei contenuti
2. Fase di richiesta del contenuto al DNS che decide l IP del datacenter migliore per me

es CDN: AKAMAI, DYN, CLOUDFLARE, LINELIGHT 